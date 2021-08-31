<template>
    <div>

        <div class="min-h-screen bg-gray-100">
            <nav class="bg-white border-b border-gray-100">
                <!-- Primary Navigation Menu -->
                <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                    <div class="flex justify-between">
                        <div class="flex">
                            <!-- Logo -->
                            <div class="flex-shrink-0 flex items-center max-h-96">
                                <inertia-link :href="route('dashboard')">
                                    <img src="images/aitvaro.jpg" alt="" class='object-contain h-48 w-full'>
                                </inertia-link>
                            </div>

                            <!-- Navigation Links -->
                            <div class="hidden space-x-8 sm:-my-px sm:ml-10 sm:flex">
                                <jet-nav-link :href="route('dashboard')" :active="route().current('dashboard')">
                                    Naujienos
                                </jet-nav-link>
                                <jet-nav-link :href="route('dashboard')" :active="route().current('structure')">
                                    Struktūra ir kontaktai
                                </jet-nav-link>
                                <jet-nav-link :href="route('dashboard')" :active="route().current('workfield')">
                                    Veiklos Sritys
                                </jet-nav-link>
                                <jet-nav-link :href="route('dashboard')" :active="route().current('administration_info')">
                                    Administracinė informacija
                                </jet-nav-link>
                            </div>
                        </div>

                    </div>
                </div>

                <!-- Responsive Navigation Menu -->
                <div :class="{'block': showingNavigationDropdown, 'hidden': ! showingNavigationDropdown}" class="sm:hidden">
                    <div class="pt-2 pb-3 space-y-1">
                        <jet-responsive-nav-link :href="route('dashboard')" :active="route().current('dashboard')">
                            Naujienos
                        </jet-responsive-nav-link>
                        <jet-responsive-nav-link :href="route('dashboard')" :active="route().current('dashboard')">
                            Struktūra ir kontaktai
                        </jet-responsive-nav-link>
                        <jet-responsive-nav-link :href="route('dashboard')" :active="route().current('dashboard')">
                            Veiklos Sritys
                        </jet-responsive-nav-link>
                        <jet-responsive-nav-link :href="route('dashboard')" :active="route().current('dashboard')">
                            Administracinė informacija
                        </jet-responsive-nav-link>
                    </div>
                </div>
            </nav>

            <!-- Page Heading -->
            <header class="bg-white shadow" v-if="$slots.header">
                <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                    <slot name="header"></slot>
                </div>
            </header>

            <!-- Page Content -->
            <main>
                <slot></slot>
            </main>
        </div>
    </div>
</template>

<script>
    import JetApplicationMark from '@/Jetstream/ApplicationMark'
    import JetBanner from '@/Jetstream/Banner'
    import JetDropdown from '@/Jetstream/Dropdown'
    import JetDropdownLink from '@/Jetstream/DropdownLink'
    import JetNavLink from '@/Jetstream/NavLink'
    import JetResponsiveNavLink from '@/Jetstream/ResponsiveNavLink'

    export default {
        components: {
            JetApplicationMark,
            JetBanner,
            JetDropdown,
            JetDropdownLink,
            JetNavLink,
            JetResponsiveNavLink,
        },

        data() {
            return {
                showingNavigationDropdown: false,
            }
        },

        methods: {
            switchToTeam(team) {
                this.$inertia.put(route('current-team.update'), {
                    'team_id': team.id
                }, {
                    preserveState: false
                })
            },

            logout() {
                this.$inertia.post(route('logout'));
            },
        }
    }
</script>
