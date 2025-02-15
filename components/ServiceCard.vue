<template>
<div class="p-4 border-sky-200 border-1 rounded-xl w-full sm:w-fit sm:max-w-[400px]">
    <div class="flex gap-2 flex-wrap">
        <h4 class="bg-zinc-100 whitespace-nowrap px-3 py-1 rounded-lg" v-for="(category, i) in  service.categories"> {{ category }} </h4>
    </div>
    
    <h3 class="font-bold my-3">{{ service.name  }}</h3>

    <p v-if="service.description" class="[word-wrap:break-word] flex-nowrap mb-5" v-html="service.description"></p>

    <p v-if="service.phones.length" class="flex gap-1 mb-3">
        <a v-for="(phone, i) in service.phones" :key="i" :href='`tel:${phone}`' class="underline text-blue-800">{{phone}}</a> 
    </p>

    

    <p v-if="service.website" class="[word-wrap:break-word] underline text-blue-800 mt-3">
        <!-- <svg version="1.1" class="mr-1" id="Layer_1" width="24" height="24" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512.044 512.044" xml:space="preserve" fill="#000000"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <rect x="446.121" y="335.111" transform="matrix(0.7071 -0.7071 0.7071 0.7071 -132.9848 440.9132)" style="fill:#25B6D2;" width="39.232" height="91.745"></rect> <polygon style="fill:#25B6D2;" points="390.254,391.574 372.462,289.165 474.871,306.957 "></polygon> </g> <path style="fill:#415E72;" d="M22.264,84.753h415.535c12.296,0,22.264,9.968,22.264,22.264V225.74 c0,12.296-9.968,22.264-22.264,22.264H22.264C9.968,248.004,0,238.036,0,225.74V107.018C0,94.722,9.968,84.753,22.264,84.753z"></path> <g> <path style="fill:#25B6D2;" d="M72.609,128.394l9.984,38.401c2.176,8.416,4.2,16.208,5.6,24h0.472 c1.712-7.648,4.2-15.76,6.696-23.864l12.32-38.529h11.52l11.696,37.745c2.808,9.04,5,16.992,6.712,24.648h0.472 c1.464-8.264,3.392-16.44,5.768-24.488l10.752-37.897h13.6l-24.336,75.489h-12.48l-11.536-36.001 c-2.664-8.144-4.904-16.424-6.712-24.8h-0.336c-1.8,8.448-4.088,16.784-6.856,24.96l-12.168,35.873h-12.48l-22.72-75.537 L72.609,128.394L72.609,128.394z"></path> <path style="fill:#25B6D2;" d="M189.251,128.394l9.984,38.401c2.176,8.416,4.2,16.208,5.6,24h0.472 c1.712-7.648,4.2-15.76,6.696-23.864l12.32-38.529h11.536l11.696,37.745c2.808,9.04,5,16.992,6.712,24.648h0.472 c1.464-8.264,3.392-16.44,5.768-24.488l10.752-37.897h13.6l-24.336,75.489h-12.52l-11.536-36.001 c-2.664-8.144-4.904-16.424-6.712-24.8h-0.312c-1.8,8.448-4.088,16.784-6.856,24.96l-12.168,35.873h-12.48l-22.736-75.537H189.251z "></path> <path style="fill:#25B6D2;" d="M305.885,128.394l9.984,38.401c2.176,8.416,4.2,16.208,5.6,24h0.472 c1.712-7.648,4.2-15.76,6.696-23.864l12.32-38.529h11.536l11.696,37.745c2.808,9.04,5,16.992,6.712,24.648h0.472 c1.464-8.264,3.392-16.44,5.768-24.488l10.752-37.897h13.6l-24.336,75.489h-12.48l-11.536-36.001 c-2.664-8.144-4.904-16.424-6.712-24.8h-0.312c-1.8,8.448-4.088,16.784-6.856,24.96l-12.168,35.873h-12.48l-22.768-75.537 L305.885,128.394L305.885,128.394z"></path> </g> </g></svg> -->
        <a :href="service.website" class="[word-wrap:break-word]" target="_blank">{{  service.website  }}</a>
    </p>

    <p v-if="service.address" class="[word-wrap:break-word] flex mt-3">
        <!-- <svg class="shrink-0 mr-1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="24" height="24" viewBox="0 0 256 256" xml:space="preserve">
            <defs>
            </defs>
            <g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: none; fill-rule: nonzero; opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)" >
                <path d="M 45 90 c -1.415 0 -2.725 -0.748 -3.444 -1.966 l -4.385 -7.417 C 28.167 65.396 19.664 51.02 16.759 45.189 c -2.112 -4.331 -3.175 -8.955 -3.175 -13.773 C 13.584 14.093 27.677 0 45 0 c 17.323 0 31.416 14.093 31.416 31.416 c 0 4.815 -1.063 9.438 -3.157 13.741 c -0.025 0.052 -0.053 0.104 -0.08 0.155 c -2.961 5.909 -11.41 20.193 -20.353 35.309 l -4.382 7.413 C 47.725 89.252 46.415 90 45 90 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: rgb(4,136,219); fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
                <path d="M 45 45.678 c -8.474 0 -15.369 -6.894 -15.369 -15.368 S 36.526 14.941 45 14.941 c 8.474 0 15.368 6.895 15.368 15.369 S 53.474 45.678 45 45.678 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: rgb(255,255,255); fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
            </g>
            </svg> -->

            <svg viewBox="0 0 1024 1024" width="24" height="24" class="icon" version="1.1" xmlns="http://www.w3.org/2000/svg" fill="#000000"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"><path d="M309.2 584.776h105.5l-49 153.2H225.8c-7.3 0-13.3-6-13.3-13.3 0-2.6 0.8-5.1 2.2-7.3l83.4-126.7c2.5-3.6 6.7-5.9 11.1-5.9z" fill="#FFFFFF"></path><path d="M404.5 791.276H225.8c-36.7 0-66.5-29.8-66.5-66.5 0-13 3.8-25.7 11-36.6l83.4-126.7c12.3-18.7 33.1-29.9 55.5-29.9h178.4l-83.1 259.7z m-95.3-206.5c-4.5 0-8.6 2.2-11.1 6l-83.4 126.7c-1.4 2.2-2.2 4.7-2.2 7.3 0 7.3 6 13.3 13.3 13.3h139.9l49-153.2H309.2z" fill="#333333"></path><path d="M454.6 584.776h109.6l25.3 153.3H429.3z" fill="#FFFFFF"></path><path d="M652.2 791.276H366.6l42.8-259.6h200l42.8 259.6z m-222.9-53.2h160.2l-25.3-153.3H454.6l-25.3 153.3z" fill="#333333"></path><path d="M618.6 584.776h105.5c4.5 0 8.6 2.2 11.1 6l83.5 126.7c4 6.1 2.3 14.4-3.8 18.4-2.2 1.4-4.7 2.2-7.3 2.2H667.7l-49.1-153.3z" fill="#FFFFFF"></path><path d="M807.6 791.276H628.9l-83.1-259.7h178.4c22.4 0 43.2 11.2 55.5 29.9l83.4 126.7c9.8 14.8 13.2 32.6 9.6 50s-13.7 32.3-28.6 42.1c-10.8 7.2-23.5 11-36.5 11z m-139.9-53.2h139.9c2.6 0 5.1-0.8 7.3-2.2 4-2.6 5.3-6.4 5.7-8.4 0.4-2 0.7-6-1.9-10l-83.4-126.6c-2.5-3.8-6.6-6-11.1-6H618.6l49.1 153.2z" fill="#333333"></path><path d="M534.1 639.7C652.5 537.4 711.7 445.8 711.7 365c0-127-102.7-212.1-195-212.1s-195 85.1-195 212.1c0 80.8 59.2 172.3 177.7 274.7 9.9 8.6 24.7 8.6 34.7 0z" fill="#8CAAFF"></path><path d="M516.7 672.7c-12.5 0-24.9-4.3-34.8-12.9C356.2 551.2 295.1 454.7 295.1 365c0-142.8 114.6-238.7 221.6-238.7S738.3 222.2 738.3 365c0 89.7-61.1 186.2-186.9 294.8-9.8 8.6-22.3 12.9-34.7 12.9z m0-493.2c-79.7 0-168.4 76.2-168.4 185.5 0 72.3 56.7 158 168.4 254.6C628.5 523 685.1 437.3 685.1 365c0-109.3-88.7-185.5-168.4-185.5z" fill="#333333"></path><path d="M516.7 348m-97.5 0a97.5 97.5 0 1 0 195 0 97.5 97.5 0 1 0-195 0Z" fill="#FFFFFF"></path><path d="M516.7 472.1c-68.4 0-124.1-55.7-124.1-124.1s55.7-124.1 124.1-124.1S640.8 279.5 640.8 348 585.1 472.1 516.7 472.1z m0-195.1c-39.1 0-70.9 31.8-70.9 70.9 0 39.1 31.8 70.9 70.9 70.9s70.9-31.8 70.9-70.9c0-39.1-31.8-70.9-70.9-70.9z" fill="#333333"></path></g></svg>
            <!-- 📍 -->
             {{ service.address  }}
    
    </p>

    <p v-if="availableSociealMedia.length" class="flex flex-col gap-1 mt-3">
        <a v-for="(socialMediaKey) in availableSociealMedia" :key="socialMediaKey" :href='service.socialMedia[socialMediaKey].link' class=" text-blue-800 underline flex items-center gap-1 mb-3">
            <svg v-if="socialMediaKey === 'instagram'"  xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="24" height="24" viewBox="0 0 48 48">
                <radialGradient id="yOrnnhliCrdS2gy~4tD8ma_Xy10Jcu1L2Su_gr1" cx="19.38" cy="42.035" r="44.899" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#fd5"></stop><stop offset=".328" stop-color="#ff543f"></stop><stop offset=".348" stop-color="#fc5245"></stop><stop offset=".504" stop-color="#e64771"></stop><stop offset=".643" stop-color="#d53e91"></stop><stop offset=".761" stop-color="#cc39a4"></stop><stop offset=".841" stop-color="#c837ab"></stop></radialGradient><path fill="url(#yOrnnhliCrdS2gy~4tD8ma_Xy10Jcu1L2Su_gr1)" d="M34.017,41.99l-20,0.019c-4.4,0.004-8.003-3.592-8.008-7.992l-0.019-20	c-0.004-4.4,3.592-8.003,7.992-8.008l20-0.019c4.4-0.004,8.003,3.592,8.008,7.992l0.019,20	C42.014,38.383,38.417,41.986,34.017,41.99z"></path><radialGradient id="yOrnnhliCrdS2gy~4tD8mb_Xy10Jcu1L2Su_gr2" cx="11.786" cy="5.54" r="29.813" gradientTransform="matrix(1 0 0 .6663 0 1.849)" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#4168c9"></stop><stop offset=".999" stop-color="#4168c9" stop-opacity="0"></stop></radialGradient><path fill="url(#yOrnnhliCrdS2gy~4tD8mb_Xy10Jcu1L2Su_gr2)" d="M34.017,41.99l-20,0.019c-4.4,0.004-8.003-3.592-8.008-7.992l-0.019-20	c-0.004-4.4,3.592-8.003,7.992-8.008l20-0.019c4.4-0.004,8.003,3.592,8.008,7.992l0.019,20	C42.014,38.383,38.417,41.986,34.017,41.99z"></path><path fill="#fff" d="M24,31c-3.859,0-7-3.14-7-7s3.141-7,7-7s7,3.14,7,7S27.859,31,24,31z M24,19c-2.757,0-5,2.243-5,5	s2.243,5,5,5s5-2.243,5-5S26.757,19,24,19z"></path><circle cx="31.5" cy="16.5" r="1.5" fill="#fff"></circle><path fill="#fff" d="M30,37H18c-3.859,0-7-3.14-7-7V18c0-3.86,3.141-7,7-7h12c3.859,0,7,3.14,7,7v12	C37,33.86,33.859,37,30,37z M18,13c-2.757,0-5,2.243-5,5v12c0,2.757,2.243,5,5,5h12c2.757,0,5-2.243,5-5V18c0-2.757-2.243-5-5-5H18z"></path>
            </svg>   

            <svg v-else-if="socialMediaKey === 'facebook'" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="24" height="24" viewBox="0 0 48 48">
                <path fill="#3F51B5" d="M42,37c0,2.762-2.238,5-5,5H11c-2.761,0-5-2.238-5-5V11c0-2.762,2.239-5,5-5h26c2.762,0,5,2.238,5,5V37z"></path><path fill="#FFF" d="M34.368,25H31v13h-5V25h-3v-4h3v-2.41c0.002-3.508,1.459-5.59,5.592-5.59H35v4h-2.287C31.104,17,31,17.6,31,18.723V21h4L34.368,25z"></path>
            </svg>
            {{service.socialMedia[socialMediaKey].title}}
        
        </a> 
    </p>
</div>
</template>

<script setup>

const props = defineProps({
    service: {}
})

const availableSociealMedia = computed(() =>
    props.service?.socialMedia && Object.keys(props.service?.socialMedia) || []
)
</script>