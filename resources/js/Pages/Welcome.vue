<template>
    <div class="min-h-screen bg-black flex items-center justify-center relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-br from-gray-900 via-black to-gray-800"></div>

        <div class="absolute inset-0 opacity-[0.02]" style="background-image: radial-gradient(circle at 2px 2px, white 1px, transparent 0); background-size: 40px 40px;"></div>

        <div class="relative z-10 max-w-sm w-full mx-4">

            <div class="text-center mb-12">
                <div class="inline-flex items-center justify-center w-16 h-16 bg-white rounded-full mb-6 shadow-lg">
                    <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-black">
                        <path d="M12 2L2 7l10 5 10-5-10-5z"/>
                        <path d="M2 17l10 5 10-5"/>
                        <path d="M2 12l10 5 10-5"/>
                    </svg>
                </div>
                <h1 class="text-3xl font-light text-white mb-2 tracking-wide">Welcome</h1>
                <p class="text-gray-400 text-sm">Join our community</p>
            </div>


            <div class="space-y-4">
                <Link
                    href="/login"
                    class="group w-full bg-white text-black py-4 px-6 rounded-2xl font-medium transition-all duration-300 hover:bg-gray-100 hover:shadow-xl hover:scale-[1.02] active:scale-[0.98] flex items-center justify-center space-x-3 border border-gray-200"
                >
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="transition-transform group-hover:scale-110">
                        <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"/>
                        <polyline points="10,17 15,12 10,7"/>
                        <line x1="15" x2="3" y1="12" y2="12"/>
                    </svg>
                    <span>Sign In</span>
                </Link>

                <Link
                    href="/register"
                    class="group w-full bg-transparent text-white py-4 px-6 rounded-2xl font-medium transition-all duration-300 hover:bg-white hover:text-black border-2 border-gray-700 hover:border-white hover:shadow-xl hover:scale-[1.02] active:scale-[0.98] flex items-center justify-center space-x-3"
                >
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="transition-transform group-hover:scale-110">
                        <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/>
                        <circle cx="9" cy="7" r="4"/>
                        <line x1="19" x2="19" y1="8" y2="14"/>
                        <line x1="22" x2="16" y1="11" y2="11"/>
                    </svg>
                    <span>Create Account</span>
                </Link>
            </div>

            <div class="text-center mt-8 text-gray-500 text-xs">
                <p>By continuing, you agree to our terms</p>
            </div>
        </div>


        <div class="absolute top-10 left-10 w-32 h-32 bg-white opacity-[0.02] rounded-full blur-xl"></div>
        <div class="absolute bottom-10 right-10 w-40 h-40 bg-white opacity-[0.01] rounded-full blur-2xl"></div>
    </div>
</template>

<script setup>
import { Link } from '@inertiajs/vue3'
</script>
