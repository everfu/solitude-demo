---
title: 隐私政策
desc: 了解本站如何收集、使用与保护访问信息
description: 了解 Solitude 演示站如何收集、使用与保护访问信息
date: 2026-08-11 00:00:00
comment: false
---

协议最新更新时间为：2026-8-11

## 隐私政策

本站非常重视用户的隐私和个人信息保护。你在使用网站时，可能会收集和使用你的相关信息。通过《隐私政策》向你说明在你访问 `solitude.efu.me` 网站时，如何收集、使用、保存、共享和转让这些信息。

## 一、在访问时如何收集和使用你的个人信息

### 在访问时，收集访问信息的服务会收集不限于以下信息：

**网络身份标识信息**（浏览器UA、IP地址）

**设备信息**

**浏览过程**（操作方式、浏览方式与时长、性能与网络加载情况）。

### 在访问时，本站内置的第三方服务会通过以下或更多途径，来获取你的以下或更多信息：

- **jsDelivr** 会收集你的访问信息，用于提供静态资源加速服务。[jsDelivr 服务条款](https://www.jsdelivr.com/terms/terms-of-service-jsdelivv)
- **LeanCloud** 会收集你的访问信息，用于存储评论与访问量数据。[LeanCloud 隐私政策](https://leancloud.cn/privacy.html)
- **GitHub** 会收集你的访问信息，用于 Giscus 评论系统的展示与提交。[GitHub 隐私政策](https://docs.github.com/zh/site-policy/privacy-policies/github-general-privacy-statement)
- **WeAvatar** 会收集你的访问信息，用于展示评论头像。[WeAvatar 隐私政策](https://weavatar.com/policy/privacy)

### 在访问时，本人仅会处于以下目的，使用你的个人信息：

- 恶意访问识别，用于维护网站
- 恶意攻击排查，用于维护网站
- 网站点击情况监测，用于优化网站页面布局方式
- 网站加载情况监测，用于优化网站性能
- 网站访问来源及访问路径，用于网站搜索结果优化
- 网站访问请求情况，用于热度数据的展示

### 第三方信息获取方将您的数据用于以下用途：

第三方可能会用于其他目的，详情请访问对应第三方服务提供的隐私协议。

### 你应该知道在你访问的时候不限于以下信息会被第三方获取并使用：

为了抵抗攻击、使用不同节点cdn加速等需求会收集不限于以下信息

<div class="table-wrap">
<table id="privacy-info-table">
<thead>
<tr><th>信息</th><th>数据</th></tr>
</thead>
<tbody>
<tr><td>IP地址</td><td class="privacy-value" id="privacy-ip">加载中...</td></tr>
<tr><td>国家</td><td class="privacy-value" id="privacy-country">加载中...</td></tr>
<tr><td>省份</td><td class="privacy-value" id="privacy-province">加载中...</td></tr>
<tr><td>城市</td><td class="privacy-value" id="privacy-city">加载中...</td></tr>
<tr><td>运营商</td><td class="privacy-value" id="privacy-isp">加载中...</td></tr>
<tr><td>操作系统</td><td class="privacy-value" id="privacy-os">加载中...</td></tr>
<tr><td>浏览器</td><td class="privacy-value" id="privacy-browser">加载中...</td></tr>
</tbody>
</table>
</div>

<script data-pjax>
(() => {
  const FALLBACK = '未能获取到信息';
  const setValue = (id, value) => {
    const el = document.getElementById(id);
    if (el) el.textContent = value || FALLBACK;
  };
  const parseAddress = (address) => {
    let rest = address || '';
    const parts = { country: '', province: '', city: '' };
    const country = rest.match(/^(.+?(?:国|地区|行政区))/);
    if (country) { parts.country = country[1]; rest = rest.slice(country[1].length); }
    const province = rest.match(/^(.+?(?:省|自治区|特别行政区|市))/);
    if (province) { parts.province = province[1]; rest = rest.slice(province[1].length); }
    const city = rest.match(/^(.+?(?:市|自治州|地区|盟))/);
    if (city) parts.city = city[1];
    return parts;
  };
  fetch('https://v2.xxapi.cn/api/ua')
    .then((res) => res.json())
    .then((data) => {
      const info = data.data || {};
      setValue('privacy-os', info.os);
      setValue('privacy-browser', info.browser ? [info.browser, info.browserVersion].filter(Boolean).join(' ') : '');
      const addr = parseAddress(info.address);
      setValue('privacy-ip', info.ip);
      setValue('privacy-country', addr.country);
      setValue('privacy-province', addr.province);
      setValue('privacy-city', addr.city);
    })
    .catch(() => {
      ['privacy-ip', 'privacy-country', 'privacy-province', 'privacy-city', 'privacy-os', 'privacy-browser'].forEach((id) => setValue(id, FALLBACK));
    });
  fetch('https://v2.xxapi.cn/api/ip')
    .then((res) => res.json())
    .then((data) => {
      const info = data.data || {};
      setValue('privacy-ip', info.ip);
      setValue('privacy-isp', info.isp);
      const addr = parseAddress(info.address);
      setValue('privacy-country', addr.country);
      setValue('privacy-province', addr.province);
      setValue('privacy-city', addr.city);
    })
    .catch(() => setValue('privacy-isp', FALLBACK));
})();
</script>

此页面展示的访问信息由 [xxapi](https://v2.xxapi.cn/) 提供的 API 获取，此页面如果未能获取到信息并不代表无法读取上述信息，以实际情况为准。

## 二、在评论时如何收集和使用你的个人信息

评论使用的是无登陆系统的匿名评论系统，你可以自愿填写真实的、或者虚假的信息作为你评论的展示信息。**鼓励你使用不易被人恶意识别的昵称进行评论**，但是建议你填写**真实的邮箱**以便收到回复（邮箱信息不会被公开）。

在你评论时，会额外收集你的详细个人与设备信息进行存储，用于鉴别恶意用户。

### 在评论时，本站内置的第三方服务会通过以下或更多途径，来获取你的相关信息：

- **WeAvatar** 会收集你的访问信息、评论填写的个人信息用于展示头像
- **GitHub** 会收集你的访问信息与评论内容，用于 Giscus 评论的存储与展示
- **LeanCloud** 会收集你的访问信息与评论内容，用于 Valine 评论的存储与展示

### 在访问时，本人仅会处于以下目的，收集并使用以下信息：

- 评论时会记录你的QQ账号（如果在邮箱位置填写QQ邮箱或QQ号），方便获取你的QQ头像。如果使用QQ邮箱但不想展示QQ头像，可以填写不含QQ号的QQ邮箱。（主动，存储）
- 评论时会记录你的邮箱，当我回复后会通过邮件通知你（主动，存储，不会公开邮箱）
- 评论时会记录你的网址，用于点击头像时快速进入你的网站（主动，存储）
- 评论时会记录你的IP地址，作为反垃圾的用户判别依据（被动，存储，不会公开IP）
- 评论会记录你的浏览器代理，用作展示系统版本、浏览器版本方便展示你使用的设备，快速定位问题（被动，存储）

## 三、如何使用 Cookies 和本地 LocalStorage 存储

本站为实现无账号评论、深色模式切换等功能，会在你的浏览器中进行本地存储，你可以随时清除浏览器中保存的所有 Cookies 以及 LocalStorage，不影响你的正常使用。

本博客中的以下业务会在你的计算机上主动存储数据：

**内置服务**

- 评论系统
- 显示模式

## 四、如何共享、转让你的个人信息

本人不会与任何公司、组织和个人共享你的隐私信息

本人不会将你的个人信息转让给任何公司、组织和个人

第三方服务的共享、转让情况详见对应服务的隐私协议

## 五、附属协议

当监测到存在恶意访问、恶意请求、恶意攻击、恶意评论的行为时，为了防止增大受害范围，可能会临时将你的ip地址及访问信息短期内添加到黑名单，短期内禁止访问。

此黑名单可能被公开，并共享给其他站点（主体并非本人）使用，包括但不限于：IP地址、设备信息、地理位置。
