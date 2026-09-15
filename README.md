# Data-calculator-app
Data Usage &amp; Expiry Calculator with AI FAQ Support Agent
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Studio & Data Hub</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        studioDark: '#131314',
                        studioSidebar: '#1e1f20',
                        studioCard: '#28292a',
                        studioBorder: '#37393b',
                        googleBlue: '#1a73e8',
                        googleBlueHover: '#1557b0'
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-studioDark text-gray-200 font-sans h-screen flex flex-col overflow-hidden">

    <!-- Top Navigation Bar -->
    <header class="h-14 border-b border-studioBorder bg-studioSidebar px-4 flex items-center justify-between shrink-0">
        <div class="flex items-center space-x-3">
            <button class="text-gray-400 hover:text-white md:hidden" id="menuBtn">
                <i class="fa-solid fa-bars text-lg"></i>
            </button>
            <div class="flex items-center space-x-2">
                <i class="fa-solid fa-wand-magic-sparkles text-googleBlue text-xl"></i>
                <span class="font-semibold text-lg text-white">AI Studio <span class="text-xs bg-blue-900 text-blue-300 px-2 py-0.5 rounded-full">Pro</span></span>
            </div>
        </div>

        <!-- Quick Action: Buy Data Button in Header -->
        <div class="flex items-center space-x-3">
            <button onclick="toggleDataModal()" class="bg-emerald-600 hover:bg-emerald-700 text-white px-3 py-1.5 rounded-lg text-sm font-medium flex items-center space-x-2 transition shadow-lg shadow-emerald-900/40">
                <i class="fa-solid fa-wifi"></i>
                <span>Buy Cheap Data</span>
            </button>
            <div class="w-8 h-8 rounded-full bg-googleBlue text-white flex items-center justify-center font-bold text-sm">
                A
            </div>
        </div>
    </header>

    <!-- Main Content Grid -->
    <div class="flex flex-1 overflow-hidden relative">

        <!-- Left Navigation Sidebar -->
        <aside class="w-64 bg-studioSidebar border-r border-studioBorder flex flex-col justify-between hidden md:flex">
            <div class="p-3 space-y-1">
                <button class="w-full bg-studioCard hover:bg-studioBorder text-white font-medium py-2 px-3 rounded-lg flex items-center space-x-3 transition border border-studioBorder">
                    <i class="fa-solid fa-plus text-googleBlue"></i>
                    <span>New Prompt</span>
                </button>
                <div class="pt-4 text-xs font-semibold text-gray-400 px-3 uppercase tracking-wider">Workspace</div>
                <a href="#" class="flex items-center space-x-3 text-gray-300 hover:bg-studioCard px-3 py-2 rounded-lg text-sm bg-studioCard border-l-2 border-googleBlue">
                    <i class="fa-solid fa-terminal text-gray-400"></i>
                    <span>Chat Playground</span>
                </a>
                <a href="#" class="flex items-center space-x-3 text-gray-400 hover:bg-studioCard hover:text-gray-200 px-3 py-2 rounded-lg text-sm">
                    <i class="fa-solid fa-sliders text-gray-400"></i>
                    <span>Tune Prompts</span>
                </a>
                <a href="#" class="flex items-center space-x-3 text-gray-400 hover:bg-studioCard hover:text-gray-200 px-3 py-2 rounded-lg text-sm">
                    <i class="fa-solid fa-key text-gray-400"></i>
                    <span>API Keys</span>
                </a>
            </div>

            <!-- Bottom Brand Quick Link -->
            <div class="p-3 border-t border-studioBorder">
                <div class="bg-studioCard p-3 rounded-xl border border-studioBorder flex items-center space-x-3">
                    <div class="bg-emerald-900/50 text-emerald-400 p-2 rounded-lg">
                        <i class="fa-solid fa-bolt"></i>
                    </div>
                    <div class="overflow-hidden">
                        <p class="text-xs text-gray-400">Powered by</p>
                        <p class="text-sm font-semibold text-white truncate">Mega Data Services</p>
                    </div>
                </div>
            </div>
        </aside>

        <!-- Center Workspace / Prompt Area -->
        <main class="flex-1 flex flex-col bg-studioDark">
            <!-- System Instructions Input -->
            <div class="p-4 border-b border-studioBorder bg-studioSidebar/40">
                <label class="block text-xs font-medium text-gray-400 uppercase tracking-wider mb-2">System Instructions</label>
                <textarea rows="2" class="w-full bg-studioDark border border-studioBorder rounded-lg p-2.5 text-sm text-gray-200 focus:outline-none focus:border-googleBlue resize-none" placeholder="You are a helpful AI assistant built to process user prompts and answer queries..."></textarea>
            </div>

            <!-- Chat / Workspace Messages -->
            <div class="flex-1 overflow-y-auto p-4 space-y-4">
                <!-- User Message -->
                <div class="flex items-start space-x-3 max-w-3xl">
                    <div class="w-8 h-8 rounded-full bg-gray-700 text-gray-200 flex items-center justify-center shrink-0">
                        <i class="fa-solid fa-user text-xs"></i>
                    </div>
                    <div class="bg-studioCard p-3.5 rounded-2xl rounded-tl-none border border-studioBorder text-sm text-gray-200">
                        Can you help me estimate how much mobile data I need for downloading 5GB files weekly?
                    </div>
                </div>

                <!-- Model Response -->
                <div class="flex items-start space-x-3 max-w-3xl">
                    <div class="w-8 h-8 rounded-full bg-googleBlue text-white flex items-center justify-center shrink-0">
                        <i class="fa-solid fa-robot text-xs"></i>
                    </div>
                    <div class="bg-studioCard/60 p-3.5 rounded-2xl rounded-tl-none border border-studioBorder text-sm text-gray-200 space-y-2">
                        <p>Downloading 5GB files weekly amounts to around **20GB to 25GB monthly** strictly for downloads, excluding general browsing and streaming.</p>
                        <div class="mt-2 p-2.5 bg-studioDark rounded-lg border border-studioBorder flex items-center justify-between">
                            <span class="text-xs text-gray-400">Need a cheap 25GB data bundle for this?</span>
                            <button onclick="toggleDataModal()" class="text-xs text-emerald-400 font-medium hover:underline flex items-center space-x-1">
                                <span>Buy Data Now</span>
                                <i class="fa-solid fa-arrow-right text-[10px]"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Prompt Input Bar -->
            <div class="p-4 border-t border-studioBorder bg-studioSidebar">
                <div class="relative flex items-center">
                    <input type="text" class="w-full bg-studioDark border border-studioBorder rounded-xl pl-4 pr-12 py-3 text-sm text-gray-200 focus:outline-none focus:border-googleBlue" placeholder="Type your prompt here...">
                    <button class="absolute right-3 text-googleBlue hover:text-googleBlueHover p-1">
                        <i class="fa-solid fa-paper-plane"></i>
                    </button>
                </div>
            </div>
        </main>

        <!-- Right Parameters Sidebar -->
        <aside class="w-72 bg-studioSidebar border-l border-studioBorder p-4 hidden lg:flex flex-col space-y-6">
            <h3 class="text-xs font-semibold text-gray-400 uppercase tracking-wider">Run Settings</h3>

            <!-- Model Selection -->
            <div>
                <label class="block text-xs text-gray-400 mb-1">Model</label>
                <select class="w-full bg-studioDark border border-studioBorder rounded-lg p-2 text-sm text-gray-200 focus:outline-none focus:border-googleBlue">
                    <option>Gemini 1.5 Pro</option>
                    <option>Gemini 1.5 Flash</option>
                </select>
            </div>

            <!-- Temperature Slider -->
            <div>
                <div class="flex justify-between text-xs mb-1">
                    <span class="text-gray-400">Temperature</span>
                    <span class="text-gray-200 font-mono">1.0</span>
                </div>
                <input type="range" min="0" max="2" step="0.1" value="1.0" class="w-full accent-googleBlue bg-studioDark">
            </div>

            <!-- Brand Fast Purchase Widget -->
            <div class="mt-auto border-t border-studioBorder pt-4">
                <h4 class="text-xs font-semibold text-gray-400 uppercase tracking-wider mb-3">Instant Top-up</h4>
                <div class="bg-studioCard p-3 rounded-xl border border-studioBorder space-y-2">
                    <p class="text-xs text-gray-300">Run out of data while testing?</p>
                    <button onclick="toggleDataModal()" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white py-2 rounded-lg text-xs font-semibold transition">
                        Buy Data Plan
                    </button>
                </div>
            </div>
        </aside>
    </div>

    <!-- DATA PURCHASE MODAL (POPUP) -->
    <div id="dataModal" class="fixed inset-0 bg-black/70 backdrop-blur-sm hidden flex items-center justify-center p-4 z-50">
        <div class="bg-studioSidebar border border-studioBorder w-full max-w-md rounded-2xl p-6 relative shadow-2xl">
            <button onclick="toggleDataModal()" class="absolute top-4 right-4 text-gray-400 hover:text-white">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>
            <div class="flex items-center space-x-2 mb-4">
                <div class="bg-emerald-600/20 text-emerald-400 p-2 rounded-lg">
                    <i class="fa-solid fa-wifi text-lg"></i>
                </div>
                <div>
                    <h3 class="font-semibold text-white">Buy Data Bundle</h3>
                    <p class="text-xs text-gray-400">Instant delivery to all networks</p>
                </div>
            </div>
            
            <form class="space-y-4" onsubmit="event.preventDefault(); alert('Order initiated!'); toggleDataModal();">
                <div>
                    <label class="block text-xs text-gray-400 mb-1">Select Network</label>
                    <select class="w-full bg-studioDark border border-studioBorder rounded-lg p-2.5 text-sm text-gray-200 focus:outline-none focus:border-googleBlue">
                        <option>MTN SME / Corporate</option>
                        <option>Airtel Data</option>
                        <option>Glo Data</option>
                        <option>9mobile Data</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs text-gray-400 mb-1">Select Data Plan</label>
                    <select class="w-full bg-studioDark border border-studioBorder rounded-lg p-2.5 text-sm text-gray-200 focus:outline-none focus:border-googleBlue">
                        <option>1GB - 30 Days</option>
                        <option>2GB - 30 Days</option>
                        <option>5GB - 30 Days</option>
                        <option>10GB - 30 Days</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs text-gray-400 mb-1">Phone Number</label>
                    <input type="tel" class="w-full bg-studioDark border border-studioBorder rounded-lg p-2.5 text-sm text-gray-200 focus:outline-none focus:border-googleBlue" placeholder="08012345678" required>
                </div>
                <button type="submit" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white py-2.5 rounded-lg text-sm font-semibold transition">
                    Proceed to Payment
                </button>
            </form>
        </div>
    </div>

    <!-- FLOATING BRAND FAQ AI AGENT WIDGET -->
    <div class="fixed bottom-20 right-5 z-40">
        <!-- Floating Toggle Icon -->
        <button onclick="toggleFaqAgent()" class="w-14 h-14 bg-googleBlue hover:bg-googleBlueHover text-white rounded-full shadow-2xl flex items-center justify-center relative transition-transform hover:scale-105">
            <i class="fa-solid fa-comments text-xl"></i>
            <span class="absolute -top-1 -right-1 bg-emerald-500 w-4 h-4 rounded-full border-2 border-studioDark"></span>
        </button>

        <!-- FAQ AI Chat Popup Box -->
        <div id="faqAgentBox" class="hidden absolute bottom-16 right-0 w-80 md:w-96 bg-studioSidebar border border-studioBorder rounded-2xl shadow-2xl flex flex-col overflow-hidden h-[420px]">
            <!-- Header -->
            <div class="bg-studioCard p-3 border-b border-studioBorder flex items-center justify-between">
                <div class="flex items-center space-x-2">
                    <div class="w-7 h-7 bg-googleBlue text-white rounded-full flex items-center justify-center text-xs">
                        <i class="fa-solid fa-robot"></i>
                    </div>
                    <div>
                        <h4 class="text-sm font-semibold text-white">Brand FAQ Support AI</h4>
                        <p class="text-[10px] text-emerald-400">Online | Instant Answers</p>
                    </div>
                </div>
                <button onclick="toggleFaqAgent()" class="text-gray-400 hover:text-white text-sm">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <!-- FAQ Chat Stream -->
            <div id="faqMessages" class="flex-1 p-3 overflow-y-auto space-y-3 text-xs">
                <div class="bg-studioCard p-2.5 rounded-lg border border-studioBorder text-gray-300">
                    👋 Hello! I'm your FAQ Agent. Ask me anything about our data plans, pricing, or payment delivery!
                </div>
            </div>

            <!-- Quick FAQ Chips -->
            <div class="px-3 py-2 border-t border-studioBorder bg-studioDark flex gap-1.5 overflow-x-auto text-[11px] whitespace-nowrap">
                <button onclick="sendFaqQuick('How long does data delivery take?')" class="bg-studioCard hover:bg-studioBorder text-gray-300 px-2.5 py-1 rounded-full border border-studioBorder">⏱️ Delivery Time?</button>
                <button onclick="sendFaqQuick('What payment methods do you accept?')" class="bg-studioCard hover:bg-studioBorder text-gray-300 px-2.5 py-1 rounded-full border border-studioBorder">💳 Payment Methods?</button>
            </div>

            <!-- Input Bar -->
            <div class="p-2 border-t border-studioBorder bg-studioCard flex items-center space-x-2">
                <input id="faqInput" type="text" placeholder="Ask a question..." class="flex-1 bg-studioDark border border-studioBorder rounded-lg px-3 py-1.5 text-xs text-white focus:outline-none focus:border-googleBlue" onkeypress="if(event.key==='Enter') sendFaqMessage()">
                <button onclick="sendFaqMessage()" class="bg-googleBlue hover:bg-googleBlueHover text-white px-3 py-1.5 rounded-lg text-xs">
                    <i class="fa-solid fa-paper-plane"></i>
                </button>
            </div>
        </div>
    </div>

    <!-- JavaScript Logic -->
    <script>
        function toggleDataModal() {
            const modal = document.getElementById('dataModal');
            modal.classList.toggle('hidden');
        }

        function toggleFaqAgent() {
            const faqBox = document.getElementById('faqAgentBox');
            faqBox.classList.toggle('hidden');
        }

        function sendFaqQuick(question) {
            document.getElementById('faqInput').value = question;
            sendFaqMessage();
        }

        function sendFaqMessage() {
            const input = document.getElementById('faqInput');
            const messagesContainer = document.getElementById('faqMessages');
            const text = input.value.trim();
            if(!text) return;

            // Render User Query
            const userMsg = document.createElement('div');
            userMsg.className = "bg-googleBlue text-white p-2.5 rounded-lg ml-auto max-w-[85%] text-xs";
            userMsg.textContent = text;
            messagesContainer.appendChild(userMsg);
            input.value = '';
            messagesContainer.scrollTop = messagesContainer.scrollHeight;

            // Simple Automated Answer Engine Demonstration
            setTimeout(() => {
                const botMsg = document.createElement('div');
                botMsg.className = "bg-studioCard p-2.5 rounded-lg border border-studioBorder text-gray-300 max-w-[85%] text-xs space-y-1";
                
                let answer = "Thank you for reaching out! Our team or automated agent will confirm your details shorty.";
                const lowerText = text.toLowerCase();
                
                if (lowerText.includes('delivery') || lowerText.includes('time')) {
                    answer = "⚡ Data delivery is instant! Once payment is verified, your phone line gets credited within 30 to 60 seconds.";
                } else if (lowerText.includes('payment') || lowerText.includes('pay')) {
                    answer = "💳 We accept automated bank transfers, debit cards, and instant wallet funding.";
                }

                botMsg.innerHTML = answer;
                messagesContainer.appendChild(botMsg);
                messagesContainer.scrollTop = messagesContainer.scrollHeight;
            }, 600);
        }
    </script>
</body>
</html>
