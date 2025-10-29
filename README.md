<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Autobiography</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&family=Playfair+Display:ital,wght@0,400..900;1,400..900&display=swap" rel="stylesheet">
    
    <link rel="icon" type="image/jpg" href="tulips.png">
    
    <style>
        /* Custom Font Definitions */
        .font-header {
            font-family: 'Playfair Display', serif;
        }
        .font-body {
            font-family: 'Inter', sans-serif;
        }

        /* --- GLOBAL BODY & BOOT SEQUENCE STYLES --- */
        body {
            background-color: #FFEFF2;
            position: relative;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 0; 
            box-sizing: border-box;
            overflow-x: hidden;
            /* Main background for the app */
            background-image: 
                radial-gradient(circle at 10% 10%, rgba(255, 255, 255, 0.6) 0%, transparent 20%),
                radial-gradient(circle at 90% 90%, rgba(255, 192, 203, 0.4) 0%, transparent 15%),
                linear-gradient(135deg, #FFDDE1 0%, #FFB6C1 100%);
            transition: background-color 0.5s ease; /* For intro transition */
        }
        
        /* --- NEW BOOT OVERLAY STYLE (Themed) --- */
        #boot-overlay {
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background: linear-gradient(135deg, #FFF0F5 0%, #FFDDE1 100%); /* Soft pink gradient */
            color: #D81B60; /* Deep Pink accent color */
            font-family: 'Inter', sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 3000;
            opacity: 1;
            transition: opacity 1s ease;
            box-shadow: inset 0 0 50px rgba(255, 192, 203, 0.5); /* Soft inner glow */
        }

        /* Container for the typing text */
        #typing-container {
            width: 80%;
            max-width: 600px;
            min-height: 100px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.9);
            border: 2px solid #FFC0CB;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(216, 27, 96, 0.1);
        }

        /* Typewriter text styling */
        .typing-line {
            white-space: nowrap;
            overflow: hidden;
            border-right: 2px solid #D81B60; /* Pink cursor */
            margin: 5px 0;
            font-size: 1rem;
            color: #6a0d2f; /* Darker pink for text */
        }
        
        /* Blinking cursor simulation */
        @keyframes blink-cursor {
            from, to { border-right-color: transparent }
            50% { border-right-color: #D81B60; }
        }
        .typing-line.blinking-cursor {
            animation: blink-cursor 0.75s step-end infinite;
        }
        
        /* The Themed Access Button */
        #access-button {
            cursor: pointer;
            margin-top: 40px;
            padding: 15px 35px;
            background: #FFC0CB; /* Light Pink */
            color: #D81B60; /* Deep Pink Text */
            border: none;
            border-radius: 10px;
            font-weight: 700;
            letter-spacing: 1px;
            box-shadow: 0 4px 15px rgba(216, 27, 96, 0.3);
            transition: all 0.3s ease;
            display: none; /* Initially hidden */
            animation: soft-pulse 2s infinite;
            font-size: 1.1rem;
        }
        #access-button:hover {
            background: #FFB6C1; /* Medium Pink */
            box-shadow: 0 6px 20px rgba(216, 27, 96, 0.4);
            transform: translateY(-2px);
        }

        @keyframes soft-pulse {
            0% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.02); opacity: 0.95; }
            100% { transform: scale(1); opacity: 1; }
        }


        /* --- APPLICATION CONTAINER STYLES --- */
        
        /* Top and Bottom Borders for Main App */
        .app-wrapper {
            position: relative;
            z-index: 10;
            width: 100%;
            max-width: 1200px;
            height: calc(100vh - 80px);
            margin-top: 40px;
            margin-bottom: 40px;
            display: flex;
            flex-direction: column;
        }

        /* Border creation */
        body::after,
        .app-border-bottom {
            content: '';
            position: fixed;
            left: 0;
            right: 0;
            height: 15px;
            background: linear-gradient(90deg, #FFC0CB, #FFB6C1, #FFF0F5);
            box-shadow: 0 3px 8px rgba(0, 0, 0, 0.1);
            z-index: 1000;
        }
        
        body::after {
            top: 0; /* Top border using ::after */
        }
        
        .app-border-bottom {
            bottom: 0; /* Bottom border using a dedicated element */
        }

        /* --- ICON AND CONTENT STYLES --- */
        .icon-button {
            background-color: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 192, 203, 0.5);
            transition: all 0.3s ease;
            text-align: left;
            border-radius: 0.75rem;
        }
        .icon-button:hover {
            transform: scale(1.03);
            box-shadow: 0 8px 20px rgba(255, 182, 193, 0.3);
        }

        /* **RECTANGULAR DIGICAM BUTTON** */
        #gallery-button.digicam-button {
            background: linear-gradient(135deg, #F5F5F5 0%, #C0C0C0 15%, #999999 40%, #DCDCDC 60%, #FFFFFF 85%, #B0B0B0 100%);
            border: 3px solid #777;
            position: relative;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
            transition: all 0.3s ease;
            height: 100px; /* Fixed height */
            min-width: 240px; 
            max-width: 100%; 
            width: 100%;
            padding: 1rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        /* Lens System - repositioned to the left */
        .digicam-lens { 
            position: absolute; 
            width: 60px; /* Smaller lens for rectangle */
            height: 60px; 
            top: 50%; 
            left: 15px; /* Left aligned */
            transform: translateY(-50%);
            background: radial-gradient(circle at center, #666 0%, #222 100%); 
            border-radius: 50%; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
            box-shadow: inset 0 0 10px rgba(0,0,0,0.8); 
            border: 3px solid #888; 
            z-index: 20;
        }
        .digicam-lens-inner { width: 75%; height: 75%; background: radial-gradient(circle at 30% 30%, #ADD8E6, #4682B4); border-radius: 50%; box-shadow: inset 0 0 15px rgba(0,0,0,0.9); }
        
        /* Viewfinder and Shutter - repositioned to the top right */
        .digicam-viewfinder { position: absolute; top: 10px; right: 50px; width: 15px; height: 10px; background-color: #333; border-radius: 2px; border: 1px solid #000; box-shadow: inset 0 0 3px rgba(0, 0, 0, 0.8); }
        .digicam-shutter { position: absolute; top: 10px; right: 15px; width: 10px; height: 10px; background-color: #FF4500; border-radius: 50%; border: 2px solid #DCDCDC; box-shadow: 0 0 5px rgba(255, 69, 0, 0.7); cursor: pointer; }
        
        /* Text - repositioned to the right */
        .digicam-button .digicam-text { 
            position: absolute; 
            top: 50%; 
            right: 15px; 
            left: auto;
            transform: translateY(-50%); 
            color: #333; 
            font-size: 1.2rem; 
            font-weight: 900; 
            letter-spacing: 2px; 
            text-shadow: 0 1px 1px rgba(255,255,255,0.7); 
            text-align: right;
            z-index: 20;
        }


        /* Modal Styles */
        .modal-backdrop {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(5px);
            z-index: 2000;
            display: none;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .modal-content {
            position: fixed;
            top: 50%; left: 50%;
            transform: translate(-50%, -50%) scale(0.95);
            background-color: white;
            z-index: 2001;
            display: none;
            opacity: 0;
            transition: all 0.3s ease;
            max-width: 90vw;
            width: 500px;
            border-radius: 0.75rem;
            border: 2px solid #FFC0CB;
        }
        #gallery-overlay-content { max-width: 90vw; width: 600px; }
        #image-viewer-overlay-content { width: 550px; max-width: 95vw; }
        /* Style for the new video viewer modal */
        #video-viewer-overlay-content { width: 800px; max-width: 95vw; }

        .modal-backdrop.show, .modal-content.show { display: block; opacity: 1; }
        .modal-content.show { transform: translate(-50%, -50%) scale(1); }
        
        .tulip-bg {
            background-image: url('https://www.transparenttextures.com/patterns/small-flowers.png');
            background-size: 100px;
            background-blend-mode: overlay;
            background-repeat: repeat;
            opacity: 0.3;
            position: absolute; top: 0; left: 0; right: 0; bottom: 0;
            z-index: -1;
            border-radius: inherit;
        }

        /* Welcome Content Block Style */
        #welcome-content-block {
            background-color: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(12px);
            border: 2px solid rgba(255, 192, 203, 0.8);
        }
        
        /* Gallery Grid Item Style */
        .grid-item {
            aspect-ratio: 1/1;
            overflow: hidden;
            border-radius: 0.5rem;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            cursor: pointer;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            background-color: #f7f7f7;
        }
        .grid-item:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 15px rgba(255, 182, 193, 0.5);
        }
        .grid-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        /* Sticky Note Style */
        #quote-sticky-note {
            background-color: #FFECB3; /* Light yellow/cream color for the note */
            border: 1px solid #FFCD38;
            box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.1), 
                         inset 0 0 5px rgba(255, 255, 255, 0.8);
            transform: rotate(2deg); /* Slight rotation for the sticky effect */
            transition: transform 0.3s ease;
        }
        #quote-sticky-note:hover {
            transform: rotate(0deg); /* Straighten on hover */
        }
        
        /* Responsive Layout Adjustments */
        @media (max-width: 1023px) { /* Adjusting breakpoints for responsiveness */
             /* On tablet/mobile, remove margin-right on the icon container */
             .main-container { margin-right: 0; }
        }
        
        @media (max-width: 767px) {
            .app-wrapper { height: auto; min-height: calc(100vh - 80px); padding: 1rem; }
            .main-content-layout { flex-direction: column; gap: 2rem; }
            #welcome-content-block { min-height: 40vh; }
            /* Mobile Digicam Adjustment */
            .digicam-button { width: 100%; height: 100px; }
            .main-container { width: 100%; align-items: center; } /* Center icons on mobile */
            .icon-button { width: 100%; max-width: 400px; }
            #quote-sticky-note { display: none; } /* Hide sticky note on small screens */
        }
        @media (min-width: 768px) {
             .main-content-layout { flex-direction: row; gap: 2rem; height: 100%; padding: 1.5rem; }
             /* The `flex-grow` on the content block handles taking up the remaining horizontal space */
             .main-container { min-width: 250px; max-width: 350px; align-self: flex-start; } 
        }
        @media (min-width: 1024px) { /* Large screen adjustments */
            /* Ensure main content layout takes up the full width minus the icon container */
            .main-content-layout { 
                justify-content: space-between; /* This spreads the icons, the main card, and the new sticky note */
                align-items: flex-start; /* Align all items to the top */
            }
            /* Make the welcome block slightly smaller to allow space for the sticky note */
            #welcome-content-block {
                max-width: 60%; 
                width: 100%;
                flex-grow: 1; /* Allows it to take up the space it needs */
            }
        }

    </style>
</head>
<body class="text-gray-800 font-body">

    <div id="boot-overlay">
        
        <h1 class="text-6xl font-header font-bold mb-10 text-center" style="color: #D81B60;">
            My Life. My OS.
        </h1>

        <div id="typing-container">
            <p id="line-0" class="typing-line blinking-cursor text-base sm:text-lg"></p>
        </div>
        
        <button id="access-button" class="flex items-center">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-unlock-keyhole mr-2">
                <path d="M10 10V6a2 2 0 0 1 4 0v4"/>
                <path d="M10 17h.01"/>
                <rect width="18" height="12" x="3" y="10" rx="2"/>
            </svg>
            Access Autobiography
        </button>

    </div>
    
    <div id="main-app-content" class="h-full w-full hidden">
        
        <div class="app-border-bottom"></div>
        
        <div class="app-wrapper">
            <div class="main-content-layout w-full h-full flex">
                
                <div class="main-container flex flex-col items-start space-y-8 p-6 flex-shrink-0">
                    
                    <button id="gallery-button" class="digicam-button rounded-2xl flex items-center justify-center p-0 overflow-hidden">
                        <div class="digicam-viewfinder"></div>
                        <div class="digicam-shutter"></div>
                        <div class="digicam-lens">
                            <div class="digicam-lens-inner"></div>
                        </div>
                        <span class="digicam-text">GALLERY</span>
                    </button>
                    
                    <div class="flex flex-col space-y-4 w-full">
                        
                        <button id="about-button" class="icon-button p-4 rounded-xl shadow-lg flex items-center justify-start w-full">
                            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="#D81B60" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-user-round flex-shrink-0">
                                <circle cx="12" cy="8" r="5"/>
                                <path d="M20 21a8 8 0 0 0-16 0"/>
                            </svg>
                            <span class="ml-4 text-lg font-semibold text-gray-700">ABOUT ME</span>
                        </button>
                        
                        <button id="contact-button" class="icon-button p-4 rounded-xl shadow-lg flex items-center justify-start w-full">
                            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="#D81B60" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-mail flex-shrink-0">
                                <rect width="20" height="16" x="2" y="4" rx="2"/>
                                <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/>
                            </svg>
                            <span class="ml-4 text-lg font-semibold text-gray-700">CONTACTS</span>
                        </button>
                    </div>

                </div>

                <div id="welcome-content-block" class="flex-grow rounded-2xl shadow-xl p-8 overflow-y-auto max-w-full lg:max-w-[650px] min-h-[400px]">
                    <div class="tulip-bg"></div>
                    <div class="relative z-10">
                        <h2 class="text-5xl font-extrabold mb-4 font-header" style="color: #D81B60;">WELCOME TO MY JOURNEY</h2>
                        <h3 class="text-xl font-semibold text-gray-700 mb-6 font-header italic">Unveiling the Chapters of a Life</h3>
                        <p class="text-gray-600 leading-relaxed space-y-4">
                            <span class="block">
                                 I reflect on my journey, I feel immense gratitude and pride. I am Messiah P. Bermudez, a 20-year-old from Bacolod City, blessed with a loving family that nurtured me with care and support. As the only girl, I was encouraged to pursue my passions and dreams with confidence.

Driven by a competitive spirit, I’ve represented my family in various competitions, earning medals, trophies, and certificates in Badminton, Dancing, Singing, Acting, and Cosplay. Academically, I’ve been recognized as an Academic Achiever, Honor Student, and Dean’s Lister, and I continue striving for excellence.

Now pursuing a BS in Information Technology at LLCC, I may be on a different path from my creative interests, but I believe this course will equip me with valuable skills for the future. I’m proud of who I’ve become and excited for the next chapter—continuing to grow, innovate, and stay thankful for every blessing.
                            </span>
                        </p>
                    </div>
                </div>
                
                <div id="quote-sticky-note" class="hidden lg:block w-[200px] h-[200px] p-4 rounded-xl shadow-lg flex-shrink-0 mt-8 cursor-pointer">
                    <div class="w-4 h-4 rounded-full bg-red-400 absolute top-[-5px] left-[-5px] shadow-sm"></div>
                    <div class="border-b-2 border-dashed border-yellow-800 pb-2 mb-2">
                            <span class="font-header font-bold text-lg text-yellow-900">Today's Motivation!</span>
                    </div>
                    <p class="text-sm italic font-body text-yellow-950 leading-snug">
                        "Why be normal when you can be the best.✨"
                        <span class="block mt-2 font-semibold text-xs text-right">— Messiah P Bermudez</span>
                    </p>
                </div>
                

            </div>
        </div>
    </div>

    <div id="gallery-overlay-backdrop" class="modal-backdrop"></div>
    <div id="gallery-overlay-content" class="modal-content p-6 rounded-lg shadow-2xl">
        <button class="modal-close-button absolute top-3 right-4 text-gray-500 hover:text-gray-800 text-3xl" data-modal="gallery-overlay">&times;</button>
        
        <div id="gallery-view-main" class="text-center font-body">
            <h3 class="text-2xl font-semibold mb-6 text-gray-800 font-header">Gallery</h3>
            <div class="flex space-x-4">
                <button id="show-images" class="flex-1 bg-pink-100 text-pink-700 font-semibold p-4 rounded-lg hover:bg-pink-200 transition">
                    IMAGES
                </button>
                <button id="show-videos" class="flex-1 bg-gray-100 text-gray-700 font-semibold p-4 rounded-lg hover:bg-gray-200 transition">
                    VIDEOS
                </button>
            </div>
        </div>
        
        <div id="gallery-view-images" class="hidden font-body">
            <button class="gallery-back-button text-pink-600 font-semibold mb-4 flex items-center">&larr; Back to Main</button>
            <h3 class="text-2xl font-semibold mb-6 text-gray-800 font-header">Images Folders</h3>
            <div class="space-y-3">
                <button data-folder="Childhood" data-media="image" class="gallery-folder-link block p-3 bg-gray-50 rounded-lg hover:bg-pink-100 transition flex items-center w-full">
                    <span class="mr-3">📁</span> Childhood
                </button>
                <button data-folder="Travels" data-media="image" class="gallery-folder-link block p-3 bg-gray-50 rounded-lg hover:bg-pink-100 transition flex items-center w-full">
                    <span class="mr-3">📁</span> Travels
                </button>
                <button data-folder="Friends & Family" data-media="image" class="gallery-folder-link block p-3 bg-gray-50 rounded-lg hover:bg-pink-100 transition flex items-center w-full">
                    <span class="mr-3">📁</span> Friends & Family
                </button>
                <button data-folder="Milestones" data-media="image" class="gallery-folder-link block p-3 bg-gray-50 rounded-lg hover:bg-pink-100 transition flex items-center w-full">
                    <span class="mr-3">📁</span> Milestones
                </button>
            </div>
        </div>
        
        <div id="gallery-view-videos" class="hidden font-body">
            <button class="gallery-back-button text-pink-600 font-semibold mb-4 flex items-center">&larr; Back to Main</button>
            <h3 class="text-2xl font-semibold mb-6 text-gray-800 font-header">Videos Folders</h3>
            <div class="space-y-3">
                <button data-folder="Vlogs" data-media="video" class="gallery-folder-link block p-3 bg-gray-50 rounded-lg hover:bg-pink-100 transition flex items-center w-full">
                    <span class="mr-3">📁</span> Vlogs
                </button>
                <button data-folder="Events" data-media="video" class="gallery-folder-link block p-3 bg-gray-50 rounded-lg hover:bg-pink-100 transition flex items-center w-full">
                    <span class="mr-3">📁</span> Events
                </button>
                <button data-folder="Memories" data-media="video" class="gallery-folder-link block p-3 bg-gray-50 rounded-lg hover:bg-pink-100 transition flex items-center w-full">
                    <span class="mr-3">📁</span> Memories
                </button>
            </div>
        </div>

        <div id="gallery-view-grid" class="hidden font-body">
            <button id="grid-back-button" data-previous-view="images" class="text-pink-600 font-semibold mb-4 flex items-center">&larr; Back to Folders</button>
            <h3 id="grid-header" class="text-2xl font-semibold mb-6 text-gray-800 font-header">Folder Name</h3>
            <div id="media-grid" class="grid grid-cols-3 gap-4 overflow-y-auto max-h-[400px]">
                </div>
        </div>
        
    </div>
    
    <div id="about-overlay-backdrop" class="modal-backdrop"></div>
    <div id="about-overlay-content" class="modal-content p-6 rounded-lg shadow-2xl max-w-md font-body">
        <button class="modal-close-button absolute top-3 right-4 text-gray-500 hover:text-gray-800 text-3xl" data-modal="about-overlay">&times;</button>
        <h3 class="text-2xl font-semibold mb-6 text-gray-800 font-header">About Me</h3>
        <div class="flex flex-col sm:flex-row gap-6 items-center">
            <img src="553698875_851721307278245_3540272616156931227_n.jpg" alt="Author" class="w-32 h-32 rounded-full shadow-md object-cover flex-shrink-0">
            <div>
                <h4 class="font-bold text-lg text-pink-600">PERSONAL INFO</h4>
                <ul class="mt-2 text-gray-600 space-y-1 list-disc list-inside">
                    <li><strong>Name:</strong> Messiah P. Bermudez</li>
                    <li><strong>Born:</strong> May 23, 2005 (Bacolod City)</li>
                    <li><strong>Occupation:</strong> College Student at LLCC</li>
                    <li><strong>Hobbies:</strong> Cooking, watching anime, reading, and drawing</li>
                </ul>
                <p class="mt-4 text-gray-500 text-sm">
                    I’m Messiah P. Bermudez, a 20-year-old from Bacolod City with a passion for creativity and learning. I enjoy exploring different talents like dancing, singing, and cosplay, and I’m currently pursuing a BS in Information Technology at LLCC to build a bright future for myself.
            </div>
        </div>
    </div>
    
    <div id="contact-overlay-backdrop" class="modal-backdrop"></div>
    <div id="contact-overlay-content" class="modal-content p-6 rounded-lg shadow-2xl max-w-md font-body">
        <button class="modal-close-button absolute top-3 right-4 text-gray-500 hover:text-gray-800 text-3xl" data-modal="contact-overlay">&times;</button>
        <h3 class="text-2xl font-semibold mb-6 text-gray-800 font-header">Contact</h3>
        <p class="text-gray-600 mb-4">Feel free to reach out. I'd love to hear from you!</p>
        <div class="space-y-4">
            <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#D81B60" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-at-sign"><circle cx="12" cy="12" r="4"/><path d="M16 8v5a3 3 0 0 0 6 0v-1a10 10 0 1 0-4 8"/></svg>
                <span class="text-gray-700">bermudez.messiah@llcc.edu.ph</span>
            </div>
            <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#D81B60" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-instagram"><rect width="20" height="20" x="2" y="2" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" x2="17.51" y1="6.5" y2="6.5"/></svg>
                <span class="text-gray-700">@quaso_23</span>
            </div>
            <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#D81B60" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-globe"><circle cx="12" cy="12" r="10"/><path d="M12 2a14.5 14.5 0 0 0 0 20 14.5 14.5 0 0 0 0-20"/><path d="M2 12h20"/></svg>
                <span class="text-gray-700">Website link of this code</span>
            </div>
        </div>
    </div>
    
    <div id="image-viewer-overlay-backdrop" class="modal-backdrop"></div>
    <div id="image-viewer-overlay-content" class="modal-content p-4 rounded-xl shadow-2xl bg-white/90 backdrop-blur-md">
        <button class="modal-close-button absolute top-2 right-3 text-gray-500 hover:text-gray-800 text-3xl z-30" data-modal="image-viewer-overlay">&times;</button>
        <div id="image-viewer-container" class="relative">
            <div class="relative bg-gray-100 rounded-lg overflow-hidden shadow-lg border-4 border-white">
                <img id="viewer-image" src="" alt="Viewed Image" class="w-full h-auto object-cover max-h-[70vh]">
            </div>
            <div class="bg-white p-3 shadow-inner mt-2 rounded-lg border border-gray-200">
                <h4 id="viewer-title" class="font-header text-xl font-bold text-pink-700 mb-1"></h4>
                <p id="viewer-stamp" class="text-xs text-gray-500 font-mono italic"></p>
            </div>
        </div>
    </div>

    <div id="video-viewer-overlay-backdrop" class="modal-backdrop"></div>
    <div id="video-viewer-overlay-content" class="modal-content p-4 rounded-xl shadow-2xl bg-white/90 backdrop-blur-md">
        <button class="modal-close-button absolute top-2 right-3 text-gray-500 hover:text-gray-800 text-3xl z-30" data-modal="video-viewer-overlay">&times;</button>
        <div id="video-viewer-container" class="relative">
            <div class="relative bg-black rounded-lg overflow-hidden shadow-lg border-4 border-white">
                <video id="viewer-video" src="" controls autoplay class="w-full h-auto max-h-[70vh]"></video>
            </div>
            <div class="bg-white p-3 shadow-inner mt-2 rounded-lg border border-gray-200">
                <h4 id="video-viewer-title" class="font-header text-xl font-bold text-pink-700 mb-1"></h4>
                <p id="video-viewer-stamp" class="text-xs text-gray-500 font-mono italic"></p>
            </div>
        </div>
    </div>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            // --- BOOT SEQUENCE ELEMENTS ---
            const bootOverlay = document.getElementById('boot-overlay');
            const mainAppContent = document.getElementById('main-app-content');
            const typingContainer = document.getElementById('typing-container');
            const accessButton = document.getElementById('access-button'); 
            
            // --- GALLERY CONSTANTS AND DOM ELEMENTS ---
            const GALLERY_VIEWS = {
                main: document.getElementById('gallery-view-main'),
                images: document.getElementById('gallery-view-images'),
                videos: document.getElementById('gallery-view-videos'),
                grid: document.getElementById('gallery-view-grid')
            };
            
            const mediaGrid = document.getElementById('media-grid');
            const gridHeader = document.getElementById('grid-header');
            const gridBackButton = document.getElementById('grid-back-button');

            // --- MODAL ELEMENTS (Updated to include Video Viewer) ---
            const modalCloseButtons = document.querySelectorAll('.modal-close-button');
            
            // Image Viewer elements
            const viewerImage = document.getElementById('viewer-image');
            const viewerTitle = document.getElementById('viewer-title');
            const viewerStamp = document.getElementById('viewer-stamp');

            // Video Viewer elements (NEW)
            const viewerVideo = document.getElementById('viewer-video');
            const videoViewerTitle = document.getElementById('video-viewer-title');
            const videoViewerStamp = document.getElementById('video-viewer-stamp');

            // ------------------------------------------------------------------
            //  THE DATA SOURCE: EDIT THIS OBJECT WITH YOUR PUBLIC IMAGE/VIDEO LINKS
            //  - The structure below defines all your media and where it lives.
            //  - Replace the placeholder URLs with direct links to your hosted files.
            // ------------------------------------------------------------------
            const REAL_MEDIA_DATA = {
                "Childhood": [
                    { 
                        type: 'image', 
                        // NOTE: This URL is a placeholder for the uploaded file 'my_first_birthday.jpg'.
                        // In a real deployment, you would replace this with the actual hosted path.
                        src: 'childhoodphoto1.jpg', 
                        title: "Church at Marigondon", 
                        stamp: "2013" 
                    },
                    { 
                        type: 'image', 
                        src: '551824468_1518294762630432_7691975797926309946_n.jpg', 
                        title: "My tenth birthday", 
                        stamp: "2013/05/23" 
                    },
                    { 
                        type: 'image', 
                        src: '564369922_1391634959192362_5208330860452488408_n.jpg', 
                        title: "", 
                        stamp: "2014" 
                    },
                    { 
                        type: 'image', 
                        src: '568291498_696590749663522_2720238543385166372_n.jpg', 
                        title: "Friend!",  
                    },
                    { 
                        type: 'image', 
                        src: '566558626_588132547691449_2882925608807736031_n.jpg', 
                        title: "Hyland Family", 
                        stamp: "2014" 
                    },
                    { 
                        type: 'image', 
                        src: '568247437_24888322180776599_2553045128425316864_n.jpg', 
                        title: "Childhood Trio!", 
                        stamp: "2014" 
                    },
                    // Add more childhood images here using the { type: 'image', src: '...', title: '...', stamp: '...' } format
                ],
                "Travels": [
                    { 
                        type: 'image', 
                        src: '504151498_699671726377211_7078629025181384401_n.jpg', 
                        title: "Tops!", 
                        stamp: "2025" 
                    },
                    { 
                        type: 'image', 
                        src: '552605733_1389556945932633_245226679973542270_n.jpg', 
                        title: "Negros Jurrasic Park!", 
                        stamp: "2024" 
                    },
                    { 
                        type: 'image', 
                        src: '553664483_1478091866822835_9001206425523899450_n.jpg', 
                        title: "CCLEX Bridge!", 
                        stamp: "10/23/2025" 
                    },
                    { 
                        type: 'image', 
                        src: '566604350_1558610728629436_6743611284867343640_n.jpg', 
                        title: "Negros Jurrasic Park!", 
                        stamp: "2024" 
                    },
                    { 
                        type: 'image', 
                        src: '568663677_806751658892482_3978526224590460915_n.jpg', 
                        title: "Island Central Mall!", 
                        stamp: "04/19/2025" 
                    },
                    { 
                        type: 'image', 
                        src: '567593181_25259862156984795_9052525064917390465_n.jpg', 
                        title: "Seaside Top Garden", 
                        stamp: "2024" 
                    },
                ],
                "Friends & Family": [
                    { 
                        type: 'image', 
                        src: '551493829_740125812420933_1778669234517700578_n.jpg', 
                        title: "AJI Modern Dance!", 
                        stamp: "2025" 
                    },
                    { 
                        type: 'image', 
                        src: '552061710_1088413076506143_3440393830465907046_n.jpg', 
                        title: "LLCC Fam!", 
                        stamp: "2024" 
                    },
                    { 
                        type: 'image', 
                        src: '566464277_1465981224512403_5194185734724087829_n.jpg', 
                        title: "Bermudez Family!", 
                        stamp: "2022" 
                    },
                    { 
                        type: 'image', 
                        src: '566542090_1171711194937525_4759158230158423935_n.jpg', 
                        title: "AJI I.T Days Competition!", 
                        stamp: "2025" 
                    },
                    { 
                        type: 'image', 
                        src: 'DSC_0883.JPG', 
                        title: "TEAM BOGO Family!", 
                        stamp: "2025" 
                    },
                    { 
                        type: 'image', 
                        src: '566661643_1489823238899591_6144268206651920261_n.jpg  ', 
                        title: "With the LOML!", 
                        stamp: "2025" 
                    },
                ],
                "Milestones": [
                    { 
                        type: 'image', 
                        src: '552707079_1517163006147396_8532708786441715845_n.jpg', 
                        title: "High School Degree Attained!", 
                        stamp: "2023" 
                    },
                    { 
                        type: 'image', 
                        src: '566469222_833744912936418_1148936862465834269_n.jpg', 
                        title: "College Intramurals!", 
                        stamp: "2023" 
                    },
                    { 
                        type: 'image', 
                        src: '566524113_803899302529711_8270930949999084509_n.jpg', 
                        title: "High School Graduation Picture!", 
                        stamp: "2023" 
                    },
                    { 
                        type: 'image', 
                        src: '569842681_1199605855411648_8285827432218674316_n.jpg', 
                        title: "Molecular Dance Champion!", 
                        stamp: "05/19/2023"
                         
                    },
                    { 
                        type: 'image', 
                        src: '574554580_3359231990912746_8278267299183778946_n.jpg', 
                        title: "ACHIEVEMENTS!!!", 
                        stamp: "2018-2025"
                    },
                    
                    { 
                        type: 'image', 
                        src: 'baba.jpg', 
                        title: "Champion In 1st Year College Cheer Dance!", 
                        stamp: "2023"
                         
                    },
                ],
                "Vlogs": [
                    { 
                        type: 'video', 
                        src: 'lv_0_20251024200014.mp4', 
                        title: "MY 18 KM CCLEX RUN!", 
                        stamp: "10/25/2025" 
                    }, 
                    { 
                        type: 'video', 
                        src: '1018.mp4', 
                        title: "Buldak Crave Vlog", 
                        stamp: "10/03/2025" 
                    }, 
                ],
                "Events": [
                    { 
                        type: 'video', 
                        src: 'Messenger_creation_1145631710098916.mp4', 
                        title: "COT Dance Competition", 
                        stamp: "05/30/2024" 
                    }, 
                    { 
                        type: 'video', 
                        src: 'VID_20241018_101531.mp4', 
                        title: "SAYAWIT competition!", 
                        stamp: "2024" 
                    }, 
                    { 
                        type: 'video', 
                        src: 'VID_20250213_155853.mp4', 
                        title: "I.T Days Dance Competition", 
                        stamp: "2024" 
                    }, 
                ],
                "Memories": [
                    { 
                        type: 'video', 
                        src: 'lv_7395831147067919632_20240922222400.mp4', 
                        title: "Badminton Edit!", 
                        stamp: "2024" 
                    }, 
                    { 
                        type: 'video', 
                        src: '2024-11-24-175419349 (1).mp4', 
                        title: "A Baddie Edit of me!", 
                        stamp: "2024" 
                    }, 
                ],
            };
            // ------------------------------------------------------------------
            // ------------------------------------------------------------------
            
            // --- BOOT SEQUENCE FUNCTIONS ---
            
            const bootLines = [
                "Initializing MyJourney OS v1.0...",
                "SYSTEM: Graphical environment loading...",
                "CHECK: Core personality signature verified [OK]",
                "CHECK: Chronological data integrity... [OK]",
                "STATUS: System ready. Awaiting user access."
            ];
            const typingSpeed = 25; // Milliseconds per character
            const pauseTime = 300;  // Pause after line finishes

            const typeLine = (lineIndex) => {
                if (lineIndex >= bootLines.length) {
                    showAccessButton();
                    return;
                }
                
                // Remove blinking cursor from the previous line
                const previousLine = document.getElementById(`line-${lineIndex - 1}`);
                if (previousLine) {
                    previousLine.classList.remove('blinking-cursor');
                }

                const lineText = bootLines[lineIndex];
                
                // Create the new line element
                const lineElement = document.createElement('p');
                lineElement.id = `line-${lineIndex}`;
                lineElement.className = 'typing-line text-base sm:text-lg';
                typingContainer.appendChild(lineElement);

                // Add blinking cursor to the current line
                lineElement.classList.add('blinking-cursor');

                let charIndex = 0;
                const timer = setInterval(() => {
                    if (charIndex < lineText.length) {
                        lineElement.textContent += lineText.charAt(charIndex);
                        charIndex++;
                    } else {
                        clearInterval(timer);
                        setTimeout(() => typeLine(lineIndex + 1), pauseTime); // Next line
                    }
                }, typingSpeed);
            };

            const showAccessButton = () => {
                // Remove the cursor from the last line
                const lastLine = document.getElementById(`line-${bootLines.length - 1}`);
                if (lastLine) {
                    lastLine.classList.remove('blinking-cursor');
                }
                accessButton.style.display = 'flex'; // Show the button
            };
            
            const finalizeBoot = () => {
                bootOverlay.style.opacity = '0';
                setTimeout(() => {
                    bootOverlay.style.display = 'none';
                    mainAppContent.classList.remove('hidden');
                }, 1000); 
            };

            // Initial call to start the boot sequence
            typeLine(0);

            // Access button event listener
            accessButton.addEventListener('click', finalizeBoot);

            // --- MODAL UTILITY FUNCTIONS ---
            const showModal = (modalId) => {
                const backdrop = document.getElementById(`${modalId}-backdrop`);
                const content = document.getElementById(`${modalId}-content`);
                
                // Ensure Gallery resets to main view when opened
                if (modalId === 'gallery-overlay') {
                    showGalleryView('main');
                }

                if (backdrop && content) {
                    backdrop.classList.add('show');
                    content.classList.add('show');
                    document.body.style.overflow = 'hidden'; 
                }
            };

            const hideModal = (modalId) => {
                const backdrop = document.getElementById(`${modalId}-backdrop`);
                const content = document.getElementById(`${modalId}-content`);

                // NEW: Handle video cleanup when closing the video modal
                if (modalId === 'video-viewer-overlay' && viewerVideo) {
                    viewerVideo.pause();
                    viewerVideo.currentTime = 0; // Rewind video on close
                }

                if (backdrop && content) {
                    content.classList.remove('show');
                    backdrop.classList.remove('show');
                    setTimeout(() => {
                        const openModals = document.querySelectorAll('.modal-backdrop.show').length;
                        if (openModals === 0) {
                            document.body.style.overflow = '';
                        }
                    }, 300); 
                }
            };

            // Attach event listeners to modal buttons
            document.getElementById('gallery-button').addEventListener('click', () => showModal('gallery-overlay'));
            document.getElementById('about-button').addEventListener('click', () => showModal('about-overlay'));
            document.getElementById('contact-button').addEventListener('click', () => showModal('contact-overlay'));
            
            modalCloseButtons.forEach(button => {
                button.addEventListener('click', (e) => {
                    // This uses the updated hideModal which handles video pausing automatically
                    hideModal(e.target.dataset.modal);
                });
            });

            // --- GALLERY LOGIC (Updated to use REAL_MEDIA_DATA) ---
            
            const showGalleryView = (viewName) => {
                // Hide all views
                Object.values(GALLERY_VIEWS).forEach(view => view.classList.add('hidden'));
                // Show the requested view
                GALLERY_VIEWS[viewName].classList.remove('hidden');
            };

            // Function to create the HTML for a single grid item
            const createGridItem = (mediaItem) => {
                const folder = mediaItem.folder || 'Gallery';
                
                // IMPORTANT: The title string must be escaped to handle special characters (like quotes)
                const safeTitle = mediaItem.title.replace(/'/g, "\\'").replace(/"/g, '\\"');
                
                if (mediaItem.type === 'image') {
                    return `
                        <div class="grid-item" onclick="handleMediaClick('image', '${mediaItem.src}', '${safeTitle}', '${mediaItem.stamp}')">
                            <img src="${mediaItem.src}" 
                                 alt="${mediaItem.title}"
                                 class="w-full h-full object-cover"/>
                        </div>
                    `;
                } else if (mediaItem.type === 'video') {
                    // Display a video icon and title on the thumbnail
                    return `
                        <div class="grid-item bg-gray-200 hover:bg-gray-300" onclick="handleMediaClick('video', '${mediaItem.src}', '${safeTitle}', '${mediaItem.stamp}')">
                            <span class="text-pink-600 text-3xl font-bold">▶️</span>
                            <span class="absolute bottom-2 text-xs text-gray-600 p-1 bg-white/70 rounded">${mediaItem.title}</span>
                        </div>
                    `;
                }
            };

            // Function to populate the grid from the REAL_MEDIA_DATA
            const populateGrid = (mediaType, folderName) => {
                gridHeader.textContent = `${folderName} ${mediaType === 'image' ? 'Images' : 'Videos'}`;
                mediaGrid.innerHTML = ''; // Clear previous content

                const mediaList = REAL_MEDIA_DATA[folderName] || []; 
                let content = '';

                mediaList.forEach((item) => {
                    if (item.type === mediaType) {
                        // Pass the entire item, which includes the folder, for creation
                        content += createGridItem(item); 
                    }
                });

                mediaGrid.innerHTML = content || '<p class="col-span-3 text-center text-gray-500 italic py-8">No items in this folder yet.</p>';
                
                gridBackButton.dataset.previousView = mediaType === 'image' ? 'images' : 'videos';
                showGalleryView('grid');
            };

            // Function to show the grid view
            const showGalleryGrid = (folderName, mediaType) => {
                populateGrid(mediaType, folderName);
            };

            // Function to handle clicks on grid items (exposed globally)
            window.handleMediaClick = (mediaType, src, title, stamp) => {
                if (mediaType === 'image') {
                    viewerImage.src = src;
                    viewerTitle.textContent = title;
                    viewerStamp.textContent = `Captured: ${stamp}`;
                    showModal('image-viewer-overlay');
                } else if (mediaType === 'video') {
                    // NEW VIDEO PLAYBACK LOGIC
                    viewerVideo.src = src;
                    videoViewerTitle.textContent = title;
                    videoViewerStamp.textContent = `Filmed: ${stamp}`;
                    showModal('video-viewer-overlay');
                }
            };


            // Event listeners for main gallery buttons
            document.getElementById('show-images').addEventListener('click', () => showGalleryView('images'));
            document.getElementById('show-videos').addEventListener('click', () => showGalleryView('videos'));
            
            // Event listener for folder links (e.g., Childhood, Travels)
            document.querySelectorAll('.gallery-folder-link').forEach(button => {
                button.addEventListener('click', (e) => {
                    const folder = e.currentTarget.dataset.folder;
                    const mediaType = e.currentTarget.dataset.media;
                    showGalleryGrid(folder, mediaType);
                });
            });

            // Event listener for gallery back buttons (from folder list to main)
            document.querySelectorAll('.gallery-back-button').forEach(button => {
                button.addEventListener('click', () => showGalleryView('main'));
            });

            // Event listener for grid back button (from grid to folder list)
            gridBackButton.addEventListener('click', (e) => {
                const previousView = e.currentTarget.dataset.previousView;
                showGalleryView(previousView);
            });
            
            // Expose show/hide modal globally for use in HTML attributes if needed
            window.showModal = showModal; 
            window.hideModal = hideModal;

        });
    </script>
</body>
</html>
