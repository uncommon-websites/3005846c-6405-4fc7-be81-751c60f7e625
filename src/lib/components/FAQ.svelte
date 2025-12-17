<script lang="ts">
  import { slide } from 'svelte/transition';
  
  interface FAQItem {
    question: string;
    answer: string;
  }

  const faqs: FAQItem[] = [
    { question: "How secure is the vault storage?", answer: "Our vault facility features climate-controlled storage, 24/7 security monitoring, and comprehensive insurance coverage. All cards are stored in their original graded cases and tracked with our proprietary inventory system." },
    { question: "How does instant trading work?", answer: "When you list a vaulted card for sale, buyers can purchase it instantly. Ownership transfers immediately in our system while the card remains secure in the vault. You can cash out or the buyer can keep it vaulted for future trading." },
    { question: "What grading companies do you accept?", answer: "We accept cards graded by PSA, BGS, CGC, SGC, and HGA. All cards must be in their original tamper-evident cases with valid certification numbers." },
    { question: "How do I send cards to the vault?", answer: "After creating an account, you'll receive shipping instructions and prepaid labels. Pack your graded cards securely and ship them to our facility. We'll verify and catalog each card upon arrival." },
    { question: "Can I get my cards back from the vault?", answer: "Absolutely. You can request withdrawal of any cards you own at any time. We'll ship them back to you securely with full insurance coverage." },
    { question: "What are the fees?", answer: "We charge a small monthly storage fee per card and a transaction fee on sales. There are no fees for depositing cards or listing them for sale. Detailed pricing is available in your account dashboard." },
    { question: "How do you determine card values?", answer: "Our marketplace uses real-time pricing data from recent sales, current listings, and market trends. Sellers set their own prices, and our system provides suggested pricing based on comparable sales." }
  ];

  let openIndex: number | null = null;

  function toggle(index: number) {
    openIndex = openIndex === index ? null : index;
  }
</script>

<section class="bg-[#f5f5f5] px-6 py-24">
  <div class="max-w-[1400px] mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12">
    <div class="lg:col-span-4">
      <h2 class="font-serif text-4xl text-gray-900 mb-6">
        Frequently asked questions
      </h2>
      <a href="/" class="text-sm text-gray-900 border-b border-gray-300 pb-0.5 hover:border-black transition-colors">See all support</a>
    </div>
    
    <div class="lg:col-span-8">
      <div class="border-t border-gray-200">
        {#each faqs as faq, i}
          <div class="border-b border-gray-200">
            <button 
              class="w-full py-6 flex justify-between items-center text-left hover:bg-gray-50 transition-colors"
              on:click={() => toggle(i)}
            >
              <span class="text-lg text-gray-800">{faq.question}</span>
              <span class="text-2xl font-light text-gray-400 ml-4">
                {openIndex === i ? '−' : '+'}
              </span>
            </button>
            {#if openIndex === i}
              <div transition:slide class="pb-6 text-gray-500 leading-relaxed">
                {faq.answer}
              </div>
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>
