<template>
    <div class="layout-topbar">
        <a class="menu-button" @click="$emit('menubutton-click')">
            <i class="pi pi-bars"></i>
        </a>
        <router-link to="/" class="logo">
            <img alt="logo" src="./assets/images/primevue-logo.png">
        </router-link>
        <div class="app-theme" v-tooltip.bottom="theme">
            <img :src="'demo/images/themes/' + logoMap[theme]" />
        </div>
        <ul ref="topbarMenu" class="topbar-menu">
            <li><router-link to="/setup">Get Started</router-link></li>
            <li class="topbar-submenu">
                <a tabindex="0" @click="toggleMenu($event, 0)">Themes</a>
                <transition name="p-connected-overlay" @enter="onMenuEnter">
                    <ul v-show="activeMenuIndex === 0">
                        <li class="topbar-submenu-header">THEMING</li>
                        <li><router-link to="/theming"><i class="pi pi-fw pi-file"/><span>Guide</span></router-link></li>
                        <li><a href="https://www.primefaces.org/designer/primevue"><i class="pi pi-fw pi-palette" /><span>Designer</span></a></li>
                        <li><a href="https://www.primefaces.org/designer-vue"><i class="pi pi-fw pi-desktop" /><span>Visual Editor</span></a></li>
                        <li><router-link to="/icons"><i class="pi pi-fw pi-info-circle"/><span>Icons</span></router-link></li>
                        <li class="topbar-submenu-header">BOOTSTRAP</li>
                        <li><a @click="changeTheme($event, 'bootstrap4-light-blue')"><img src="demo/images/themes/bootstrap4-light-blue.svg" alt="Blue Light" /><span>Blue Light</span></a></li>
                        <li><a @click="changeTheme($event, 'bootstrap4-light-purple')"><img src="demo/images/themes/bootstrap4-light-purple.svg" alt="Purple Light" /><span>Purple Light</span></a></li>
                        <li><a @click="changeTheme($event, 'bootstrap4-dark-blue', true)"><img src="demo/images/themes/bootstrap4-dark-blue.svg" alt="Blue Dark" /><span>Blue Dark</span></a></li>
                        <li><a @click="changeTheme($event, 'bootstrap4-dark-purple', true)"><img src="demo/images/themes/bootstrap4-dark-purple.svg" alt="Purple Dark" /><span>Purple Dark</span></a></li>

                        <li class="topbar-submenu-header">MATERIAL DESIGN</li>
                        <li><a @click="changeTheme($event, 'md-light-indigo')"><img src="demo/images/themes/md-light-indigo.svg" alt="Indigo Light" /><span>Indigo Light</span></a></li>
                        <li><a @click="changeTheme($event, 'md-light-deeppurple')"><img src="demo/images/themes/md-light-deeppurple.svg" alt="Deep Purple Light" /><span>Deep Purple Light</span></a></li>
                        <li><a @click="changeTheme($event, 'md-dark-indigo', true)"><img src="demo/images/themes/md-dark-indigo.svg" alt="Indigo Dark" /><span>Indigo Dark</span></a></li>
                        <li><a @click="changeTheme($event, 'md-dark-deeppurple', true)"><img src="demo/images/themes/md-dark-deeppurple.svg" alt="Deep Purple Dark" /><span>Deep Purple Dark</span></a></li>

                        <li class="topbar-submenu-header">MATERIAL DESIGN COMPACT</li>
                        <li><a @click="changeTheme($event, 'mdc-light-indigo')"><img src="demo/images/themes/md-light-indigo.svg" alt="Indigo Light" /><span>Indigo Light</span></a></li>
                        <li><a @click="changeTheme($event, 'mdc-light-deeppurple')"><img src="demo/images/themes/md-light-deeppurple.svg" alt="Deep Purple Light" /><span>Deep Purple Light</span></a></li>
                        <li><a @click="changeTheme($event, 'mdc-dark-indigo', true)"><img src="demo/images/themes/md-dark-indigo.svg" alt="Indigo Dark" /><span>Indigo Dark</span></a></li>
                        <li><a @click="changeTheme($event, 'mdc-dark-deeppurple', true)"><img src="demo/images/themes/md-dark-deeppurple.svg" alt="Deep Purple Dark" /><span>Deep Purple Dark</span></a></li>

                        <li class="topbar-submenu-header">FLUENT UI</li>
                        <li><a @click="changeTheme($event, 'fluent-light')"><img src="demo/images/themes/fluent-light.png" alt="Fluent Light" /><span>Fluent Light</span></a></li>

                        <li class="topbar-submenu-header">PRIMEONE</li>
                        <li><a @click="changeTheme($event, 'saga-blue')"><img src="demo/images/themes/saga-blue.png" alt="Saga Blue" /><span>Saga Blue</span></a></li>
                        <li><a @click="changeTheme($event, 'saga-green')"><img src="demo/images/themes/saga-green.png" alt="Saga Green" /><span>Saga Green</span></a></li>
                        <li><a @click="changeTheme($event, 'saga-orange')"><img src="demo/images/themes/saga-orange.png" alt="Saga Orange" /><span>Saga Orange</span></a></li>
                        <li><a @click="changeTheme($event, 'saga-purple')"><img src="demo/images/themes/saga-purple.png" alt="Saga Purple" /><span>Saga Purple</span></a></li>
                        <li><a @click="changeTheme($event, 'vela-blue', true)"><img src="demo/images/themes/vela-blue.png" alt="Vela Blue" /><span>Vela Blue</span></a></li>
                        <li><a @click="changeTheme($event, 'vela-green', true)"><img src="demo/images/themes/vela-green.png" alt="Vela Green" /><span>Vela Green</span></a></li>
                        <li><a @click="changeTheme($event, 'vela-orange', true)"><img src="demo/images/themes/vela-orange.png" alt="Vela Orange" /><span>Vela Orange</span></a></li>
                        <li><a @click="changeTheme($event, 'vela-purple', true)"><img src="demo/images/themes/vela-purple.png" alt="Vela Purple" /><span>Vela Purple</span></a></li>
                        <li><a @click="changeTheme($event, 'arya-blue', true)"><img src="demo/images/themes/arya-blue.png" alt="Arya Blue" /><span>Arya Blue</span></a></li>
                        <li><a @click="changeTheme($event, 'arya-green', true)"><img src="demo/images/themes/arya-green.png" alt="Arya Green" /><span>Arya Green</span></a></li>
                        <li><a @click="changeTheme($event, 'arya-orange', true)"><img src="demo/images/themes/arya-orange.png" alt="Arya Orange" /><span>Arya Orange</span></a></li>
                        <li><a @click="changeTheme($event, 'arya-purple', true)"><img src="demo/images/themes/arya-purple.png" alt="Arya Purple" /><span>Arya Purple</span></a></li>

                        <li class="topbar-submenu-header">PREMIUM</li>
                        <li><a @click="changeTheme($event, 'soho-light')"><img src="demo/images/themes/soho-light.png" alt="Soho Light" /><span>Soho Light</span></a></li>
                        <li><a @click="changeTheme($event, 'soho-dark', true)"><img src="demo/images/themes/soho-dark.png" alt="Soho Dark" /><span>Soho Dark</span></a></li>
                        <li><a @click="changeTheme($event, 'mira')"><img src="demo/images/themes/mira.jpg" alt="Mira" /><span>Mira</span></a></li>
                        <li><a @click="changeTheme($event, 'nano')"><img src="demo/images/themes/nano.jpg" alt="Nano" /><span>Nano</span></a></li>

                        <li class="topbar-submenu-header">LEGACY</li>
                        <li><a @click="changeTheme($event, 'nova')"><img src="demo/images/themes/nova.png" alt="Nova" /><span>Nova</span></a></li>
                        <li><a @click="changeTheme($event, 'nova-alt')"><img src="demo/images/themes/nova-alt.png" alt="Nova Alt" /><span>Nova Alt</span></a></li>
                        <li><a @click="changeTheme($event, 'nova-accent')"><img src="demo/images/themes/nova-accent.png" alt="Nova Accent" /><span>Nova Accent</span></a></li>
                        <li><a @click="changeTheme($event, 'nova-vue')"><img src="demo/images/themes/nova-vue.png" alt="Nova Vue" /><span>Nova Vue</span></a></li>
                        <li><a @click="changeTheme($event, 'luna-amber', true)"><img src="demo/images/themes/luna-amber.png" alt="Luna Amber" /><span>Luna Amber</span></a></li>
                        <li><a @click="changeTheme($event, 'luna-blue', true)"><img src="demo/images/themes/luna-blue.png" alt="Luna Blue" /><span>Luna Blue</span></a></li>
                        <li><a @click="changeTheme($event, 'luna-green', true)"><img src="demo/images/themes/luna-green.png" alt="Luna Green" /><span>Luna Green</span></a></li>
                        <li><a @click="changeTheme($event, 'luna-pink', true)"><img src="demo/images/themes/luna-pink.png" alt="Luna Pink" /><span>Luna Pink</span></a></li>
                        <li><a @click="changeTheme($event, 'rhea')"><img src="demo/images/themes/rhea.png" alt="Rhea" /><span>Rhea</span></a></li>
                    </ul>
                </transition>
            </li>
            <li class="topbar-submenu">
                <a tabindex="0" @click="toggleMenu($event, 1)">Templates</a>
                <transition name="p-connected-overlay" @enter="onMenuEnter">
                    <ul v-show="activeMenuIndex === 1">
                        <li class="topbar-submenu-header">FREE ADMIN TEMPLATE</li>
                        <li><a href="https://www.primefaces.org/sigma-vue"><img src="./assets/images/layouts/themeswitcher-sigma.png" alt="Sigma" /><span>Sigma</span></a></li>
                        <li class="topbar-submenu-header">PREMIUM ADMIN TEMPLATES</li>
                        <li><a href="https://www.primefaces.org/layouts/sapphire-vue"><img src="./assets/images/layouts/themeswitcher-sapphire.png" alt="Sapphire" /><span>Sapphire</span><span class="theme-badge material">material</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/serenity-vue"><img src="./assets/images/layouts/themeswitcher-serenity.png" alt="Serenity" /><span>Serenity</span><span class="theme-badge material">material</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/ultima-vue"><img src="./assets/images/layouts/themeswitcher-ultima.png" alt="Ultima" /><span>Ultima</span><span class="theme-badge material">material</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/avalon-vue"><img src="./assets/images/layouts/themeswitcher-avalon.png" alt="Avalon" /><span>Avalon</span><span class="theme-badge bootstrap">bootstrap</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/babylon-vue"><img src="./assets/images/layouts/themeswitcher-babylon.png" alt="Babylon" /><span>Babylon</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/apollo-vue"><img src="./assets/images/layouts/themeswitcher-apollo.png" alt="Apollo" /><span>Apollo</span><span class="theme-badge darkmode">dark mode</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/roma-vue"><img src="./assets/images/layouts/themeswitcher-roma.jpg" alt="Roma" /><span>Roma</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/prestige-vue"><img src="./assets/images/layouts/themeswitcher-prestige.png" alt="Prestige" /><span>Prestige</span></a></li>
                    </ul>
                </transition>
            </li>
            <li class="topbar-submenu topbar-resources-submenu">
                <a tabindex="0" @click="toggleMenu($event, 2)">Resources</a>
                <transition name="p-connected-overlay" @enter="onMenuEnter">
                    <ul v-show="activeMenuIndex === 2">
                        <li><router-link to="/support"><span>Support</span></router-link></li>
                        <li><a href="https://forum.primefaces.org/viewforum.php?f=110"><span>Forum</span></a></li>
                        <li><a href="https://discord.gg/gzKFYnpmCY" target="_blank"><span>Discord Chat</span></a></li>
                        <li><a href="https://github.com/primefaces/primevue/tree/2.x" target="_blank"><span>Source Code</span></a></li>
                        <li><a href="https://www.primefaces.org/store" target="_blank"><span>PrimeStore</span></a></li>
                        <li><a href="https://www.primefaces.org/category/primevue/" target="_blank"><span>Blog</span></a></li>
                        <li><a href="https://twitter.com/primevue?lang=en" target="_blank"><span>Twitter</span></a></li>
                        <li><a href="https://www.primefaces.org/whouses" target="_blank"><span>Who Uses</span></a></li>
                        <li><a href="https://www.primefaces.org/newsletter" target="_blank"><span>Newsletter</span></a></li>
                        <li><a href="https://www.primetek.com.tr" target="_blank"><span>About PrimeTek</span></a></li>
                    </ul>
                </transition>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    outsideClickListener: null,
    darkDemoStyle: null,
    watch: {
        $route() {
            this.activeMenuIndex = null;
        }
    },
    props: {
        theme: null
    },
    data() {
        return {
            activeMenuIndex: null,
            logoMap: {
                'bootstrap4-light-blue': 'bootstrap4-light-blue.svg',
                'bootstrap4-light-purple': 'bootstrap4-light-purple.svg',
                'bootstrap4-dark-blue': 'bootstrap4-dark-blue.svg',
                'bootstrap4-dark-purple': 'bootstrap4-dark-purple.svg',
                'md-light-indigo': 'md-light-indigo.svg',
                'md-light-deeppurple': 'md-light-deeppurple.svg',
                'md-dark-indigo': 'md-dark-indigo.svg',
                'md-dark-deeppurple': 'md-dark-deeppurple.svg',
                'mdc-light-indigo': 'md-light-indigo.svg',
                'mdc-light-deeppurple': 'md-light-deeppurple.svg',
                'mdc-dark-indigo': 'md-dark-indigo.svg',
                'mdc-dark-deeppurple': 'md-dark-deeppurple.svg',
                'saga-blue': 'saga-blue.png',
                'saga-green': 'saga-green.png',
                'saga-orange': 'saga-orange.png',
                'saga-purple': 'saga-purple.png',
                'vela-blue': 'vela-blue.png',
                'vela-green': 'vela-green.png',
                'vela-orange': 'vela-orange.png',
                'vela-purple': 'vela-purple.png',
                'arya-blue': 'arya-blue.png',
                'arya-green': 'arya-green.png',
                'arya-orange': 'arya-orange.png',
                'arya-purple': 'arya-purple.png',
                'nova': 'nova.png',
                'nova-alt': 'nova-alt.png',
                'nova-accent': 'nova-accent.png',
                'nova-vue': 'nova-vue.png',
                'luna-blue': 'luna-blue.png',
                'luna-green': 'luna-green.png',
                'luna-pink': 'luna-pink.png',
                'luna-amber': 'luna-amber.png',
                'rhea': 'rhea.png',
                'fluent-light': 'fluent-light.png',
                'soho-light': 'soho-light.png',
                'soho-dark': 'soho-dark.png',
                'mira': 'mira.jpg',
                'nano': 'nano.jpg'
            }
        }
    },
    methods: {
        changeTheme(event, theme, dark) {
            this.$emit('change-theme', {theme: theme, dark: dark});
            this.activeMenuIndex = null;
            event.preventDefault();
        },
        toggleMenu(event, index) {
            this.activeMenuIndex = (this.activeMenuIndex === index) ? null : index;
            event.preventDefault();
        },
        onMenuEnter() {
            this.bindOutsideClickListener();
        },
        bindOutsideClickListener() {
            if (!this.outsideClickListener) {
                this.outsideClickListener = (event) => {
                    if ((this.activeMenuIndex != null && this.isOutsideTopbarMenuClicked(event))) {
                        this.activeMenuIndex = null;
                        this.unbindOutsideClickListener();
                    }
                };
                document.addEventListener('click', this.outsideClickListener);
            }
        },
        unbindOutsideClickListener() {
            if (this.outsideClickListener) {
                document.removeEventListener('click', this.outsideClickListener);
                this.outsideClickListener = null;
            }
        },
        isOutsideTopbarMenuClicked(event) {
            return !(this.$refs.topbarMenu.isSameNode(event.composedPath()[0]) || this.$refs.topbarMenu.contains(event.composedPath()[0]));
        }
    }
}
</script>
