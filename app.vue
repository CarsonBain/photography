<template>
  <div class="flex flex-col h-full min-h-screen">
    <div class="w-full max-w-screen-lg pt-10 pb-16 px-6 md:px-16 mx-auto flex flex-col flex-1">
      <header class="flex-grow-0 flex-shrink-0 basis-auto">
        <nav class="flex justify-between items-center">
          <NuxtLink class="font-extrabold text-xl md:text-3xl uppercase tracking-wide" to="/">Carson Bain</NuxtLink>
          <div>
            <ul class="flex list-none space-x-3">
              <li>
                <NuxtLink
                  class="md:text-lg font-semibold py-1"
                  activeClass="border-b-2 border-solid border-current"
                  to="/"
                >
                  Work
                </NuxtLink>
              </li>
              <li>
                <NuxtLink
                  class="md:text-lg font-semibold py-1"
                  activeClass="border-b-2 border-solid border-current"
                  to="/about"
                >
                  About
                </NuxtLink>
              </li>
            </ul>
          </div>
        </nav>
      </header>
      <main class="relative mt-8 md:mt-16 flex flex-col items-center flex-grow shrink-0 basis-auto">
        <NuxtPage></NuxtPage>
      </main>
      <footer
        class="mt-16 text-xs text-gray-700 flex-grow-0 flex-shrink-0 basis-auto flex flex-col items-center space-y-2"
      >
        <p>© {{ new Date().getFullYear() }} Carson Bain</p>
        <p>
          <a class="underline" target="_blank" href="https://www.instagram.com/carsonbain/"> @carsonbain</a>
        </p>
      </footer>
    </div>
  </div>
</template>
<script setup>
// TODO: should this piece of state live here? maybe if it gets more complex abstract to a different file
const allGalleries = useState('allGalleries', () => []);
const homePageImages = useState('homePageImages', () => []);
const { getEntriesForContentType } = useEntries();
await useAsyncData(async () => {
  const data = await getEntriesForContentType('homePage');
  homePageImages.value = data[0].fields.collageImages;
  // const data = await getEntriesForContentType('gallery');
  // allGalleries.value = data;
});
</script>
