<template>
  <div class="vip">
    <h1 class="vip-title">{{ lang === 'zh-CN' ? 'VIP服务' : 'VIP Service' }}</h1>
    <p class="vip-sub-title" v-if="lang === 'zh-CN'">
      为了更好的服务开发者，现开通&nbsp;<span>VIP答疑通道</span>&nbsp;和&nbsp;<span>定制化服务</span>。
    </p>
    <p class="vip-sub-title" v-else>In order to better serve developers, we have now opened <span>VIP Q&A</span> and <span>Custom Service</span> .</p>
    <div class="vip-content">
      <div class="vip-content-item">
        <h3 class="vip-content-item-title">{{ lang === 'zh-CN' ? 'VIP答疑' : 'VIP Q&A' }}</h3>
        <p class="vip-content-item-sub-title">{{ lang === 'zh-CN' ? '专属微信VIP群解答疑难问题' : 'Exclusive wechat VIP group to answer difficult questions' }}</p>
        <template v-if="diffDate">
          <p
            style="font-size: 14px;padding-bottom: 14px;font-family: Arial, Helvetica, sans-serif;"
            v-if="diffDate && lang === 'zh-CN'">
            限时特价&nbsp;&nbsp;
            <span v-if="diffDate.d > 0">
              {{ diffDate.d }}<span style="padding-left: 2px;padding-right:2px;">天</span>
            </span>
            <span v-if="diffDate.d > 0 || diffDate.h > 0">
              {{ diffDate.h > 9 ? diffDate.h : `0${diffDate.h}` }}<span style="padding-left: 3px;padding-right:3px;">小时</span>
            </span>
            <span v-if="diffDate.d > 0 || diffDate.h > 0 || diffDate.m > 0">
              {{ diffDate.m > 9 ? diffDate.m : `0${diffDate.m}` }}<span style="padding-left: 3px;padding-right:3px;">分</span>
            </span>
            <span>
              {{ diffDate.s > 9 ? diffDate.s : `0${diffDate.s}` }}<span style="padding-left: 3px;">秒</span>
            </span>
          </p>
          <p
            style="font-size: 14px;padding-bottom: 14px;font-family: Arial, Helvetica, sans-serif;"
            v-else>
            Special offer  {{ diffDate.d }}:{{ diffDate.h > 9 ? diffDate.h : `0${diffDate.h}` }}:{{ diffDate.m > 9 ? diffDate.m : `0${diffDate.m}` }}:{{ diffDate.s > 9 ? diffDate.s : `0${diffDate.s}` }}
          </p>
        </template>
        
        <p class="vip-content-item-price">
          {{ lang === 'zh-CN' ? `${diffDate ? '¥ 300.00' : '¥ 500.00'}` : `${diffDate ? '$ 48.00' : '$ 78.00'}` }}<span v-if="diffDate" class="vip-content-item-original-price">{{ lang === 'zh-CN' ? '¥ 500.00' : '$ 78.00' }}</span>
        </p>
        <ul class="vip-content-item-access-list">
          <li>
            <svg class="vip-content-item-icon" viewBox="0 0 1024 1024">
              <path d="M512.506025 6.906294c-278.758842 0-505.57773 226.820935-505.57773 505.579777 0 278.797727 226.781026 505.576707 505.57773 505.576707 278.797727 0 505.57773-226.77898 505.57773-505.576707C1018.083755 233.727229 791.303752 6.906294 512.506025 6.906294L512.506025 6.906294zM807.507806 412.036287l-331.285149 334.883093c-0.081864 0.081864-0.246617 0.127913-0.334621 0.25378-0.12075 0.079818-0.12075 0.245593-0.246617 0.328481-2.644223 2.562359-5.915733 4.133134-8.977465 5.876847-1.527796 0.865717-2.771113 2.189875-4.387937 2.808976-4.962012 1.987261-10.213619 3.022847-15.473413 3.022847-5.296633 0-10.631128-1.035586-15.637142-3.105734-1.653663-0.700965-2.980891-2.109034-4.551666-2.978844-3.061732-1.736551-6.244214-3.269463-8.895601-5.872754-0.081864-0.079818-0.125867-0.251733-0.207731-0.333598-0.081864-0.119727-0.245593-0.119727-0.328481-0.246617l-162.930813-167.443593c-15.928784-16.383132-15.555278-42.569538 0.827855-58.499345 16.382109-15.889899 42.531676-15.597233 58.504462 0.827855l133.51076 137.193639L748.712725 353.823468c16.054651-16.257266 42.285059-16.419971 58.505485-0.327458C823.391565 369.5875 823.55427 395.782092 807.507806 412.036287L807.507806 412.036287zM807.507806 412.036287"/>
            </svg>
            {{ lang === 'zh-CN' ? '专属微信VIP群' : 'Exclusive wechat VIP group' }}
          </li>
          <li>
            <svg class="vip-content-item-icon" viewBox="0 0 1024 1024">
              <path d="M512.506025 6.906294c-278.758842 0-505.57773 226.820935-505.57773 505.579777 0 278.797727 226.781026 505.576707 505.57773 505.576707 278.797727 0 505.57773-226.77898 505.57773-505.576707C1018.083755 233.727229 791.303752 6.906294 512.506025 6.906294L512.506025 6.906294zM807.507806 412.036287l-331.285149 334.883093c-0.081864 0.081864-0.246617 0.127913-0.334621 0.25378-0.12075 0.079818-0.12075 0.245593-0.246617 0.328481-2.644223 2.562359-5.915733 4.133134-8.977465 5.876847-1.527796 0.865717-2.771113 2.189875-4.387937 2.808976-4.962012 1.987261-10.213619 3.022847-15.473413 3.022847-5.296633 0-10.631128-1.035586-15.637142-3.105734-1.653663-0.700965-2.980891-2.109034-4.551666-2.978844-3.061732-1.736551-6.244214-3.269463-8.895601-5.872754-0.081864-0.079818-0.125867-0.251733-0.207731-0.333598-0.081864-0.119727-0.245593-0.119727-0.328481-0.246617l-162.930813-167.443593c-15.928784-16.383132-15.555278-42.569538 0.827855-58.499345 16.382109-15.889899 42.531676-15.597233 58.504462 0.827855l133.51076 137.193639L748.712725 353.823468c16.054651-16.257266 42.285059-16.419971 58.505485-0.327458C823.391565 369.5875 823.55427 395.782092 807.507806 412.036287L807.507806 412.036287zM807.507806 412.036287"/>
            </svg>
            {{ lang === 'zh-CN' ? '及时响应，快速答疑' : 'Timely response and quick Q&A' }}
          </li>
          <li>
            <svg class="vip-content-item-icon" viewBox="0 0 1024 1024">
              <path d="M512.506025 6.906294c-278.758842 0-505.57773 226.820935-505.57773 505.579777 0 278.797727 226.781026 505.576707 505.57773 505.576707 278.797727 0 505.57773-226.77898 505.57773-505.576707C1018.083755 233.727229 791.303752 6.906294 512.506025 6.906294L512.506025 6.906294zM807.507806 412.036287l-331.285149 334.883093c-0.081864 0.081864-0.246617 0.127913-0.334621 0.25378-0.12075 0.079818-0.12075 0.245593-0.246617 0.328481-2.644223 2.562359-5.915733 4.133134-8.977465 5.876847-1.527796 0.865717-2.771113 2.189875-4.387937 2.808976-4.962012 1.987261-10.213619 3.022847-15.473413 3.022847-5.296633 0-10.631128-1.035586-15.637142-3.105734-1.653663-0.700965-2.980891-2.109034-4.551666-2.978844-3.061732-1.736551-6.244214-3.269463-8.895601-5.872754-0.081864-0.079818-0.125867-0.251733-0.207731-0.333598-0.081864-0.119727-0.245593-0.119727-0.328481-0.246617l-162.930813-167.443593c-15.928784-16.383132-15.555278-42.569538 0.827855-58.499345 16.382109-15.889899 42.531676-15.597233 58.504462 0.827855l133.51076 137.193639L748.712725 353.823468c16.054651-16.257266 42.285059-16.419971 58.505485-0.327458C823.391565 369.5875 823.55427 395.782092 807.507806 412.036287L807.507806 412.036287zM807.507806 412.036287"/>
            </svg>
            {{ lang === 'zh-CN' ? '更多的示例代码' : 'More sample code' }}
          </li>
          <li>
            <svg class="vip-content-item-icon" viewBox="0 0 1024 1024">
              <path d="M512.506025 6.906294c-278.758842 0-505.57773 226.820935-505.57773 505.579777 0 278.797727 226.781026 505.576707 505.57773 505.576707 278.797727 0 505.57773-226.77898 505.57773-505.576707C1018.083755 233.727229 791.303752 6.906294 512.506025 6.906294L512.506025 6.906294zM807.507806 412.036287l-331.285149 334.883093c-0.081864 0.081864-0.246617 0.127913-0.334621 0.25378-0.12075 0.079818-0.12075 0.245593-0.246617 0.328481-2.644223 2.562359-5.915733 4.133134-8.977465 5.876847-1.527796 0.865717-2.771113 2.189875-4.387937 2.808976-4.962012 1.987261-10.213619 3.022847-15.473413 3.022847-5.296633 0-10.631128-1.035586-15.637142-3.105734-1.653663-0.700965-2.980891-2.109034-4.551666-2.978844-3.061732-1.736551-6.244214-3.269463-8.895601-5.872754-0.081864-0.079818-0.125867-0.251733-0.207731-0.333598-0.081864-0.119727-0.245593-0.119727-0.328481-0.246617l-162.930813-167.443593c-15.928784-16.383132-15.555278-42.569538 0.827855-58.499345 16.382109-15.889899 42.531676-15.597233 58.504462 0.827855l133.51076 137.193639L748.712725 353.823468c16.054651-16.257266 42.285059-16.419971 58.505485-0.327458C823.391565 369.5875 823.55427 395.782092 807.507806 412.036287L807.507806 412.036287zM807.507806 412.036287"/>
            </svg>
            {{ lang === 'zh-CN' ? '首页赞助商广告位' : 'Homepage sponsor advertising space' }}
          </li>
        </ul>
        <p class="vip-content-item-tip" v-if="lang === 'zh-CN'">
          在&nbsp;<a class="vip-content-item-link" target="_blank" rel="noreferrer" href="/sponsor.html">赞助页</a>&nbsp;对项目进行捐赠，完成之后联系开发者加入专属VIP群。
        </p>
        <p class="vip-content-item-tip" v-else>
          Sponsor the project on the <a class="vip-content-item-link" target="_blank" rel="noreferrer" href="/en-US/sponsor.html">sponsor page</a>, and after completion, contact the developer to join the exclusive VIP group.
        </p>
      </div>
      <div class="vip-content-item">
        <h3 class="vip-content-item-title">{{ lang === 'zh-CN' ? '定制化服务' : 'Custom Service' }}</h3>
        <p class="vip-content-item-sub-title">{{ lang === 'zh-CN' ? '专属定制，扩展开发' : 'Exclusive customization and extended development' }}</p>
        <p class="vip-content-item-price">
          {{ lang === 'zh-CN' ? '¥ 面议' : '$ Discussion' }}
        </p>
        <ul class="vip-content-item-access-list">
          <li>
            <svg class="vip-content-item-icon" viewBox="0 0 1024 1024">
              <path d="M512.506025 6.906294c-278.758842 0-505.57773 226.820935-505.57773 505.579777 0 278.797727 226.781026 505.576707 505.57773 505.576707 278.797727 0 505.57773-226.77898 505.57773-505.576707C1018.083755 233.727229 791.303752 6.906294 512.506025 6.906294L512.506025 6.906294zM807.507806 412.036287l-331.285149 334.883093c-0.081864 0.081864-0.246617 0.127913-0.334621 0.25378-0.12075 0.079818-0.12075 0.245593-0.246617 0.328481-2.644223 2.562359-5.915733 4.133134-8.977465 5.876847-1.527796 0.865717-2.771113 2.189875-4.387937 2.808976-4.962012 1.987261-10.213619 3.022847-15.473413 3.022847-5.296633 0-10.631128-1.035586-15.637142-3.105734-1.653663-0.700965-2.980891-2.109034-4.551666-2.978844-3.061732-1.736551-6.244214-3.269463-8.895601-5.872754-0.081864-0.079818-0.125867-0.251733-0.207731-0.333598-0.081864-0.119727-0.245593-0.119727-0.328481-0.246617l-162.930813-167.443593c-15.928784-16.383132-15.555278-42.569538 0.827855-58.499345 16.382109-15.889899 42.531676-15.597233 58.504462 0.827855l133.51076 137.193639L748.712725 353.823468c16.054651-16.257266 42.285059-16.419971 58.505485-0.327458C823.391565 369.5875 823.55427 395.782092 807.507806 412.036287L807.507806 412.036287zM807.507806 412.036287"/>
            </svg>
            {{ lang === 'zh-CN' ? 'VIP答疑所有服务' : 'VIP Q&A all services' }}
          </li>
          <li>
            <svg class="vip-content-item-icon" viewBox="0 0 1024 1024">
              <path d="M512.506025 6.906294c-278.758842 0-505.57773 226.820935-505.57773 505.579777 0 278.797727 226.781026 505.576707 505.57773 505.576707 278.797727 0 505.57773-226.77898 505.57773-505.576707C1018.083755 233.727229 791.303752 6.906294 512.506025 6.906294L512.506025 6.906294zM807.507806 412.036287l-331.285149 334.883093c-0.081864 0.081864-0.246617 0.127913-0.334621 0.25378-0.12075 0.079818-0.12075 0.245593-0.246617 0.328481-2.644223 2.562359-5.915733 4.133134-8.977465 5.876847-1.527796 0.865717-2.771113 2.189875-4.387937 2.808976-4.962012 1.987261-10.213619 3.022847-15.473413 3.022847-5.296633 0-10.631128-1.035586-15.637142-3.105734-1.653663-0.700965-2.980891-2.109034-4.551666-2.978844-3.061732-1.736551-6.244214-3.269463-8.895601-5.872754-0.081864-0.079818-0.125867-0.251733-0.207731-0.333598-0.081864-0.119727-0.245593-0.119727-0.328481-0.246617l-162.930813-167.443593c-15.928784-16.383132-15.555278-42.569538 0.827855-58.499345 16.382109-15.889899 42.531676-15.597233 58.504462 0.827855l133.51076 137.193639L748.712725 353.823468c16.054651-16.257266 42.285059-16.419971 58.505485-0.327458C823.391565 369.5875 823.55427 395.782092 807.507806 412.036287L807.507806 412.036287zM807.507806 412.036287"/>
            </svg>
            {{ lang === 'zh-CN' ? '根据需求组件定制开发' : 'Customized development based on required components' }}
          </li>
        </ul>
        <p class="vip-content-item-tip">
          {{ lang === 'zh-CN' ? '联系开发者，讨论具体需求。' : 'Contact developers to discuss specific requirements.' }}
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { useData } from 'vitepress'

const { lang } = useData()

const diffDate = ref(null)

onMounted(() => {
  const countdown = () => {
    const time = new Date().getTime();
    const endTime = new Date('2024-05-01').getTime()
    const diff = endTime - time
    if (diff > 0) {
      const d = Math.floor(diff / 24 / 60 / 60 / 1000)
      const h = Math.floor((diff % (24 * 60 * 60 * 1000)) / 60 / 60 / 1000)
      const m = Math.floor((diff % (60 * 60 * 1000)) / 60 / 1000)
      const s = Math.floor((diff % (60 * 1000)) / 1000)
      diffDate.value = { d, h, m, s }
      setTimeout(() => {
        countdown()
      }, 1000)
    } else {
      diffDate.value = null
    }
  }
  countdown()
})

</script>
<style scoped>
.vip-title {
  font-size: 50px;
  text-align: center;
  font-weight: bold;
  line-height: normal;
  letter-spacing: 4px;
}
.vip-sub-title {
  font-size: 30px;
  font-weight: bold;
  text-align: center;
  padding: 10px 16px 50px 16px;
  letter-spacing: 1px;
  line-height: 42px;
  color: var(--vp-c-text-2);
}

.vip-sub-title span {
  color: transparent;
  background-image: linear-gradient(to right, var(--custom-green), var(--vp-c-indigo-1));
  background-clip: text;
}

.vip-content {
  display: flex;
  justify-content: center;
  gap: 20px;
  padding: 10px 60px 80px 60px;
}

.vip-content-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 50%;
  border-radius: 20px;
  padding: 30px 20px;
  border: 1px solid var(--vp-c-bg-soft);
  background-color: var(--vp-c-bg-soft);
  transition: border-color 0.25s, background-color 0.25s;
  cursor: pointer;
  max-width: 580px;
}

.vip-content-item:hover {
  border-color: var(--vp-c-indigo-1);
  background-color: var(--vp-c-indigo-soft);
}

.vip-content-item-title {
  font-size: 28px;
  font-weight: bold;
  text-align: center;
  letter-spacing: 2px;
  line-height: normal;
}

.vip-content-item-sub-title {
  font-size: 16px;
  text-align: center;
  padding-top: 6px;
  padding-bottom: 26px;
  color: var(--vp-c-text-2);
}

.vip-content-item-price {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 38px;
  font-weight: bold;
  text-align: center;
  padding: 0 0 30px 0;
}

.vip-content-item-original-price {
  font-size: 20px;
  color: var(--vp-c-text-2);
  text-decoration: line-through var(--vp-c-text-2);
  margin-left: 6px;
  font-weight: normal;
}

.vip-content-item-access-list {
  display: flex;
  flex-direction: column;
  margin: 0;
}

.vip-content-item-access-list li {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.vip-content-item-icon {
  fill: var(--vp-c-indigo-1);
  width: 16px;
  height: 16px;
  margin-right: 12px;
}

.vip-content-item-tip {
  padding-top: 30px;
  font-size: 14px;
  color: #e77c0a;
  line-height: 18px;
}

.vip-content-item-link {
  color: var(--vp-c-indigo-1);
  text-decoration: underline;
}

@media (max-width: 960px) {
  .vip-content {
    padding-left: 16px;
    padding-right: 16px;
  }

  .vip-content {
    flex-direction: column;
  }
  .vip-content-item {
    width: 100%;
    max-width: inherit;
  }
}

</style>