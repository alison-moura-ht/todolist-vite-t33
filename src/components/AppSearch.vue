<template>
    <div class="max-w-md mx-auto rounded-full flex items-center bg-white">
        <div class="w-full">
            <input
                type="search"
                class="px-4 py-1 w-full rounded-full focus:outline-none"
                placeholder="search"
                x-model="search"
            />
        </div>
        <div>
            <button
                type="submit"
                class="w-12 h-12 rounded-full flex justify-center items-center text-white bg-gray-600"
            >
                <svg
                    class="w-5 h-5"
                    fill="none"
                    stroke="currentColor"
                    viewBox="0 0 24 24"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
                    />
                </svg>
            </button>
        </div>
    </div>
</template>