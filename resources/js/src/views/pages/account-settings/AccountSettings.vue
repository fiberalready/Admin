<template>
  <v-card id="account-setting-card">
    <!-- tabs -->
    <v-tabs v-model="tab" show-arrows>
      <v-tab v-for="tab in tabs" :key="tab.icon">
        <v-icon size="20" class="me-3">
          {{ tab.icon }}
        </v-icon>
        <span>{{ tab.title }}</span>
      </v-tab>
    </v-tabs>

    <!-- tabs item -->
    <v-tabs-items v-model="tab">
      <v-tab-item>
        <account-settings-account :account-data="accountSettingData.account"></account-settings-account>
      </v-tab-item>

      <v-tab-item>
        <account-settings-security></account-settings-security>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>

<script>
import { mdiAccountOutline, mdiLockOpenOutline } from '@mdi/js'
import { ref } from '@vue/composition-api'

// demos
import AccountSettingsAccount from './AccountSettingsAccount.vue'
import AccountSettingsSecurity from './AccountSettingsSecurity.vue'

export default {
  components: {
    AccountSettingsAccount,
    AccountSettingsSecurity,
  },
  setup() {
    const tab = ref('')

    // tabs
    const tabs = [
      { title: 'Account', icon: mdiAccountOutline },
      { title: 'Security', icon: mdiLockOpenOutline },
    ]

    // account settings data
    const accountSettingData = {
      account: {
        avatarImg: require('@/assets/images/avatars/1.png').default,
        username: 'johnDoe',
        name: 'john Doe',
        email: 'johnDoe@example.com',
        role: 'Admin',
        status: 'Active',
        company: 'Google.inc',
      },
    }

    return {
      tab,
      tabs,
      accountSettingData,
      icons: {
        mdiAccountOutline,
        mdiLockOpenOutline,
      },
    }
  },
}
</script>
