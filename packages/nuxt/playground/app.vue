<template>
  <div style="min-height: 1000vh">
    <BAlert :model-value="true">
      Hello World
    </BAlert>
    <BToastOrchestrator />
    <BModalOrchestrator />
    <BModal v-model="show">
      Nuxt module playground!
    </BModal>
    <BButton @click="show = !show">
      Click me
    </BButton>
    <img
      src="@/assets/logo.png"
      width="50"
      alt="Bootstrap logo"
    >
    <BImg
      src="@/assets/logo.png"
      width="50"
      alt="Bootstrap logo"
    />
    {{ f }}
    {{ toast }}
    <BButton @click="toast.show({ props: { title: 'Hello World!' } })">
      Show Global Toast
    </BButton>
    <BFormSelect
      v-model="formSelectMultipleSelected"
      class="mb-3"
      multiple
    >
      <template #first>
        <BFormSelectOption
          :value="null"
          disabled
        >
          -- Please select an option --
        </BFormSelectOption>
      </template>
      <BFormSelectOption value="C">
        Option C
      </BFormSelectOption>
      <BFormSelectOption value="D">
        Option D
      </BFormSelectOption>
    </BFormSelect>
    <BCollapse
      id="collapse-1"
      class="mt-2"
    >
      <template #header="{ visible, toggle, id }">
        <h4>Custom Header</h4>
        <p>Visible: {{ visible }}</p>
        <BButton
          variant="primary"
          :aria-expanded="visible"
          :aria-controls="id"
          @click="toggle"
        >
          Toggle
        </BButton>
      </template>
      <BCard v-b-color-mode="'light'">
        <p class="card-text">
          Collapse contents Here
        </p>
        <BButton
          v-b-toggle.collapse-1-inner
          size="sm"
        >
          Toggle Inner Collapse with directive
        </BButton>
        <BCollapse
          id="collapse-1-inner"
          class="mt-2"
        >
          <BCard>Hello!</BCard>
        </BCollapse>
      </BCard>
    </BCollapse>
    <BCard title="foobar">
      bar foo
    </BCard>
    <BContainer class="mt-5">
      <BRow>
        <BCol>
          <BLink
            :to="{ path: '/about' }"
            variant="info"
          >
            About
          </BLink>
        </BCol>
      </BRow>
      <BRow>
        <BCol>
          <BLink
            to="/"
            variant="primary"
            prefetch
          >
            Home
          </BLink>
        </BCol>
      </BRow>
      <BRow>
        <BCol>
          <BLink
            href="https://google.com"
            target="_blank"
            variant="danger"
          >
            Google
          </BLink>
        </BCol>
      </BRow>
      <BRow>
        <BCol>
          <BLink
            :to="{ path: '/about' }"
            prefetched-class="link-underline-danger"
            variant="info"
          >
            About with prefetch underline class
          </BLink>
        </BCol>
      </BRow>
      <BRow>
        <BCol>
          Nav items
          <BNavItem :to="{ path: '/about' }">
            About
          </BNavItem>
          <BNavItem to="/">
            Home
          </BNavItem>
        </BCol>
      </BRow>
      <BRow>
        <BCol>
          dropdown
          <BDropdown>
            <BDropdownItem to="/">
              Home
            </BDropdownItem>
            <BDropdownItem to="/about">
              About
            </BDropdownItem>
          </BDropdown>
        </BCol>
      </BRow>
      <BRow class="mt-3 border">
        <BCol>
          <NuxtPage />
        </BCol>
      </BRow>
    </BContainer>
  </div>
</template>

<script setup>
const show = ref(false)

const f = useBreadcrumb()
useColorMode()
useModal()
useModalController()
const toast = useToastController()
const formSelectMultipleSelected = ref([])
</script>
