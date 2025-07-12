<template>
    <div class="min-h-screen bg-black">
        <nav class="bg-gray-900 border-b border-gray-800">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex justify-between h-16">

                    <div class="flex items-center space-x-4">
                        <div class="flex items-center space-x-3">
                            <div class="w-8 h-8 bg-white rounded-full flex items-center justify-center">
                                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-black">
                                    <path d="M12 2L2 7l10 5 10-5-10-5z"/>
                                    <path d="M2 17l10 5 10-5"/>
                                    <path d="M2 12l10 5 10-5"/>
                                </svg>
                            </div>
                            <h1 class="text-xl font-light text-white">Dashboard</h1>
                        </div>
                    </div>

                    <div class="flex items-center space-x-6">

                        <div class="flex items-center space-x-3">
                            <div class="w-8 h-8 bg-gray-700 rounded-full flex items-center justify-center overflow-hidden">
                                <img
                                    v-if="$page.props.auth?.user.avatar"
                                    :src="`/storage/${$page.props.auth.user.avatar}`"
                                    :alt="$page.props.auth.user.name"
                                    class="w-full h-full object-cover"
                                >
                                <svg
                                    v-else
                                    width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-gray-300"
                                >
                                    <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/>
                                    <circle cx="12" cy="7" r="4"/>
                                </svg>
                            </div>
                            <span class="text-gray-300 text-sm">
                                Welcome, <span class="text-white font-medium">{{ $page.props.auth?.user.name || 'User' }}</span>
                            </span>
                        </div>

                        <button
                            @click="logout"
                            class="group flex items-center space-x-2 bg-gray-800 text-gray-300 px-4 py-2 rounded-xl hover:bg-red-900 hover:text-red-200 transition-all duration-300 hover:scale-105 active:scale-95"
                        >
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="transition-transform group-hover:scale-110">
                                <path d="M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h4"/>
                                <polyline points="16,17 21,12 16,7"/>
                                <line x1="21" x2="9" y1="12" y2="12"/>
                            </svg>
                            <span class="text-sm font-medium">{{ isLoggingOut ? 'Logging out...' : 'Logout' }}</span>
                        </button>

                    </div>
                </div>
            </div>
        </nav>

        <div class="max-w-7xl mx-auto py-8 sm:px-6 lg:px-8">
            <div class="px-4 sm:px-0">
                <div class="bg-gray-900 border border-gray-800 rounded-3xl p-8 mb-8 relative overflow-hidden">

                    <div class="absolute top-0 right-0 w-40 h-40 bg-white opacity-[0.02] rounded-full blur-2xl"></div>
                    <div class="absolute bottom-0 left-0 w-32 h-32 bg-white opacity-[0.01] rounded-full blur-xl"></div>

                    <div class="relative z-10 text-center">
                        <div class="inline-flex items-center justify-center w-16 h-16 bg-white rounded-full mb-6">
                            <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-black">
                                <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
                                <polyline points="9,22 9,12 15,12 15,22"/>
                            </svg>
                        </div>
                        <h2 class="text-3xl font-light text-white mb-4">Welcome to your Dashboard!</h2>
                        <p class="text-gray-400 text-lg">You are successfully logged in and ready to explore.</p>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">

                    <div class="bg-gray-900 border border-gray-800 rounded-2xl p-6 hover:bg-gray-800 transition-all duration-300 hover:scale-105 cursor-pointer group">
                        <div class="flex items-center space-x-4">
                            <div class="w-12 h-12 bg-blue-500 bg-opacity-20 rounded-xl flex items-center justify-center group-hover:bg-opacity-30 transition-all duration-300">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-blue-400">
                                <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
                                <polyline points="14,2 14,8 20,8"/>
                                <line x1="16" x2="8" y1="13" y2="13"/>
                                <line x1="16" x2="8" y1="17" y2="17"/>
                                <polyline points="10,9 9,9 8,9"/>
                                </svg>
                            </div>
                            <div>
                                <h3 class="text-white font-medium">Documents</h3>
                                <p class="text-gray-400 text-sm">Manage your files</p>
                            </div>
                        </div>
                    </div>

                    <div class="bg-gray-900 border border-gray-800 rounded-2xl p-6 hover:bg-gray-800 transition-all duration-300 hover:scale-105 cursor-pointer group">
                        <div class="flex items-center space-x-4">
                            <div class="w-12 h-12 bg-green-500 bg-opacity-20 rounded-xl flex items-center justify-center group-hover:bg-opacity-30 transition-all duration-300">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-green-400">
                                <path d="M9 19c-5 0-8-4-8-9 0-5 3-9 8-9 3 0 5 2 5 5v.5L20 12l-5 4v.5c0 3-2 5-5 5z"/>
                                <path d="M22 12h-4l-3 4 2 5-2 1-5-5-4-5 1-5 5-2z"/>
                                </svg>
                            </div>
                            <div>
                                <h3 class="text-white font-medium">Analytics</h3>
                                <p class="text-gray-400 text-sm">View your stats</p>
                            </div>
                        </div>
                    </div>

                    <div class="bg-gray-900 border border-gray-800 rounded-2xl p-6 hover:bg-gray-800 transition-all duration-300 hover:scale-105 cursor-pointer group">
                        <div class="flex items-center space-x-4">
                            <div class="w-12 h-12 bg-purple-500 bg-opacity-20 rounded-xl flex items-center justify-center group-hover:bg-opacity-30 transition-all duration-300">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-purple-400">
                                <path d="M12.22 2h-.44a2 2 0 0 0-2 2v.18a2 2 0 0 1-1 1.73l-.43.25a2 2 0 0 1-2 0l-.15-.08a2 2 0 0 0-2.73.73l-.22.38a2 2 0 0 0 .73 2.73l.15.1a2 2 0 0 1 1 1.72v.51a2 2 0 0 1-1 1.74l-.15.09a2 2 0 0 0-.73 2.73l.22.38a2 2 0 0 0 2.73.73l.15-.08a2 2 0 0 1 2 0l.43.25a2 2 0 0 1 1 1.73V20a2 2 0 0 0 2 2h.44a2 2 0 0 0 2-2v-.18a2 2 0 0 1 1-1.73l.43-.25a2 2 0 0 1 2 0l.15.08a2 2 0 0 0 2.73-.73l.22-.39a2 2 0 0 0-.73-2.73l-.15-.08a2 2 0 0 1-1-1.74v-.5a2 2 0 0 1 1-1.74l.15-.09a2 2 0 0 0 .73-2.73l-.22-.38a2 2 0 0 0-2.73-.73l-.15.08a2 2 0 0 1-2 0l-.43-.25a2 2 0 0 1-1-1.73V4a2 2 0 0 0-2-2z"/>
                                <circle cx="12" cy="12" r="3"/>
                                </svg>
                            </div>
                            <div>
                                <h3 class="text-white font-medium">Settings</h3>
                                <p class="text-gray-400 text-sm">Manage preferences</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="bg-gray-900 border border-gray-800 rounded-2xl p-6">
                    <div class="flex items-center space-x-3 mb-6">
                        <div class="w-10 h-10 bg-gray-800 rounded-xl flex items-center justify-center">
                            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-gray-300">
                                <circle cx="12" cy="12" r="10"/>
                                <polyline points="12,6 12,12 16,14"/>
                            </svg>
                        </div>
                        <h3 class="text-xl font-medium text-white">Recent Activity</h3>
                    </div>

                    <div class="space-y-4">
                        <div class="flex items-center space-x-4 p-4 bg-gray-800 bg-opacity-50 rounded-xl">
                            <div class="w-8 h-8 bg-blue-500 bg-opacity-20 rounded-full flex items-center justify-center">
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-blue-400">
                                    <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"/>
                                    <polyline points="10,17 15,12 10,7"/>
                                    <line x1="15" x2="3" y1="12" y2="12"/>
                                </svg>
                            </div>
                            <div class="flex-1">
                                <p class="text-white text-sm">Successfully logged in</p>
                                <p class="text-gray-400 text-xs">Just now</p>
                            </div>
                        </div>

                        <div class="flex items-center justify-center py-8 text-gray-500">
                            <div class="text-center">
                                <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mx-auto mb-2 opacity-50">
                                    <path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"/>
                                    <path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"/>
                                </svg>
                                <p class="text-sm">More activity will appear here as you use the app</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="fixed inset-0 opacity-[0.02] pointer-events-none" style="background-image: radial-gradient(circle at 2px 2px, white 1px, transparent 0); background-size: 40px 40px;"></div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import { router } from '@inertiajs/vue3'

const isLoggingOut = ref(false)

const logout = () => {
    isLoggingOut.value = true
    router.post('/logout', {
        onFinish: () => {
            isLoggingOut.value = false
        },
    })
}
</script>
