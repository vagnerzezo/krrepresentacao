<template>
 <section class="bg-white py-16 px-4">
   <div class="max-w-7xl mx-auto">
     <!-- Título -->
     <h2 class="text-center text-xl font-bold uppercase mb-12">
       Depoimentos de Parceiros
     </h2>

     <!-- Grid de depoimentos -->
     <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
       <div
         v-for="index in 3"
         :key="index"
         class=""
       >
         <p class="bg-gray-100 rounded-3xl p-6 text-sm text-gray-800">
           Lorem Ipsum is simply dummy text of the printing and typesetting
           industry. Lorem Ipsum has been the industry's standard dummy text
           ever since the 1500s, when an unknown printer took a galley of type
           and scrambled it to make a type specimen book. It has survived not
           only five centuries, but also the leap into electronic typesetting,
           remaining essentially unchanged.
         </p>

         <!-- Avatar -->
         <div class="flex items-center gap-4 mt-6">
           <img
             src="/img/user.svg"
             alt="André Masseratto"
             class="w-12 h-12 rounded-full object-cover"
           />
           <div>
             <p class="font-bold uppercase text-sm">André Masseratto</p>
             <p class="text-xs text-gray-600">Executivo - Westcoast</p>
           </div>
         </div>
       </div>
     </div>
   </div>
 </section>
</template>