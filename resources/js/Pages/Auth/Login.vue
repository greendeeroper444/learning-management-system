<template>
    <div class="min-h-screen bg-black flex items-center justify-center relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-br from-gray-900 via-black to-gray-800"></div>

        <div class="absolute inset-0 opacity-[0.02]" style="background-image: radial-gradient(circle at 2px 2px, white 1px, transparent 0); background-size: 40px 40px;"></div>

        <div class="relative z-10 max-w-md w-full mx-4">
            <div class="text-center mb-10">
                <div class="inline-flex items-center justify-center w-12 h-12 bg-white rounded-full mb-4 shadow-lg">
                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-black">
                        <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/>
                        <circle cx="9" cy="7" r="4"/>
                        <line x1="19" x2="19" y1="8" y2="14"/>
                        <line x1="22" x2="16" y1="11" y2="11"/>
                    </svg>
                </div>
                <h2 class="text-2xl font-light text-white mb-2">Welcome Back</h2>
                <p class="text-gray-400 text-sm">Enter our community today</p>
            </div>

            <form @submit.prevent="submit" class="space-y-6">

                <div class="group">
                    <label for="email" class="block text-sm font-medium text-gray-300 mb-2">
                        Email Address
                    </label>
                    <div class="relative">
                        <div class="absolute inset-y-0 left-0 pl-4 flex items-center pointer-events-none">
                            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-gray-500">
                                <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
                                <polyline points="22,6 12,13 2,6"/>
                            </svg>
                        </div>
                        <input
                            id="email"
                            v-model="form.email"
                            type="email"
                            required
                            class="w-full pl-12 pr-4 py-4 bg-gray-900 border border-gray-700 rounded-2xl text-white placeholder-gray-500 focus:outline-none focus:border-white focus:ring-2 focus:ring-white focus:ring-opacity-20 transition-all duration-300"
                            :class="{ 'border-red-500 focus:border-red-500 focus:ring-red-500': errors.email }"
                            placeholder="Enter your email"
                        >
                    </div>
                    <p v-if="errors.email" class="text-red-400 text-sm mt-2 flex items-center">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-1">
                            <circle cx="12" cy="12" r="10"/>
                            <line x1="12" x2="12" y1="8" y2="12"/>
                            <line x1="12" x2="12.01" y1="16" y2="16"/>
                        </svg>
                        {{ errors.email }}
                    </p>
                </div>

                <div class="group">
                    <label for="password" class="block text-sm font-medium text-gray-300 mb-2">
                        Password
                    </label>
                    <div class="relative">
                        <div class="absolute inset-y-0 left-0 pl-4 flex items-center pointer-events-none">
                            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-gray-500">
                                <rect width="18" height="11" x="3" y="11" rx="2" ry="2"/>
                                <path d="M7 11V7a5 5 0 0 1 10 0v4"/>
                            </svg>
                        </div>
                        <input
                            id="password"
                            v-model="form.password"
                            type="password"
                            required
                            class="w-full pl-12 pr-4 py-4 bg-gray-900 border border-gray-700 rounded-2xl text-white placeholder-gray-500 focus:outline-none focus:border-white focus:ring-2 focus:ring-white focus:ring-opacity-20 transition-all duration-300"
                            :class="{ 'border-red-500 focus:border-red-500 focus:ring-red-500': errors.password }"
                            placeholder="Create a password"
                        >
                    </div>
                    <p v-if="errors.password" class="text-red-400 text-sm mt-2 flex items-center">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-1">
                            <circle cx="12" cy="12" r="10"/>
                            <line x1="12" x2="12" y1="8" y2="12"/>
                            <line x1="12" x2="12.01" y1="16" y2="16"/>
                        </svg>
                        {{ errors.password }}
                    </p>
                </div>

                <button
                    type="submit"
                    :disabled="form.processing"
                    class="group w-full bg-white text-black py-4 px-6 rounded-2xl font-medium transition-all duration-300 hover:bg-gray-100 hover:shadow-xl hover:scale-[1.02] active:scale-[0.98] disabled:opacity-50 disabled:cursor-not-allowed disabled:hover:scale-100 flex items-center justify-center space-x-3"
                >
                    <svg v-if="form.processing" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="animate-spin">
                        <path d="M21 12a9 9 0 11-6.219-8.56"/>
                    </svg>
                    <svg v-else width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="transition-transform group-hover:scale-110">
                        <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/>
                        <circle cx="9" cy="7" r="4"/>
                        <line x1="19" x2="19" y1="8" y2="14"/>
                        <line x1="22" x2="16" y1="11" y2="11"/>
                    </svg>
                    <span>{{ form.processing ? 'Logging in...' : 'Login' }}</span>
                </button>
            </form>

            <div class="text-center mt-8">
                <Link
                    href="/register"
                    class="text-gray-400 hover:text-white transition-colors duration-300 text-sm flex items-center justify-center space-x-2"
                >
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"/>
                        <polyline points="10,17 15,12 10,7"/>
                        <line x1="15" x2="3" y1="12" y2="12"/>
                    </svg>
                    <span>Don't have an account? Sign up</span>
                </Link>
            </div>
        </div>

        <div class="absolute top-10 left-10 w-32 h-32 bg-white opacity-[0.02] rounded-full blur-xl"></div>
        <div class="absolute bottom-10 right-10 w-40 h-40 bg-white opacity-[0.01] rounded-full blur-2xl"></div>
    </div>
</template>

<script setup>
import { useForm, Link } from '@inertiajs/vue3'

const props = defineProps({
    errors: {
        type: Object,
        default: () => ({})
    }
})

const form = useForm({
    email: '',
    password: '',
    remember: false,
})

const submit = () => {
    form.post('/login')
}
</script>
