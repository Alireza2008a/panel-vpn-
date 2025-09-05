this project for example .
code<->
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>پنل VPN - خرید و مدیریت</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;600;700&display=swap');

        * {
            font-family: 'Vazirmatn', sans-serif;
        }

        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .card-hover {
            transition: all 0.3s ease;
        }

        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }

        .pulse-animation {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        .form-input {
            transition: all 0.3s ease;
        }

        .form-input:focus {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.3);
        }

        .payment-method {
            transition: all 0.3s ease;
        }

        .payment-method:hover {
            transform: translateY(-2px);
        }

        .payment-method.selected {
            border-color: #8b5cf6;
            background-color: rgba(139, 92, 246, 0.1);
        }
    </style>
</head>
<body class="bg-gray-900 text-white">
    <!-- Header -->
    <header class="gradient-bg shadow-lg">
        <div class="container mx-auto px-4 py-4">
            <div class="flex justify-between items-center">
                <div class="flex items-center space-x-4 space-x-reverse">
                    <div class="w-10 h-10 bg-white rounded-full flex items-center justify-center cursor-pointer" onclick="showPage('home')">
                        <span class="text-purple-600 font-bold text-xl">V</span>
                    </div>
                    <h1 class="text-2xl font-bold cursor-pointer" onclick="showPage('home')">پنل VPN</h1>
                </div>
                <div class="flex items-center space-x-4 space-x-reverse">
                    <div class="relative">
                        <button onclick="showPage('cart')" class="bg-white bg-opacity-20 p-2 rounded-lg hover:bg-opacity-30 transition-all">
                            🛒 سبد خرید (<span id="cartCount">0</span>)
                        </button>
                    </div>
                    <div id="authButtons">
                        <button onclick="showPage('login')" class="bg-white bg-opacity-20 px-4 py-2 rounded-lg hover:bg-opacity-30 transition-all ml-2">
                            ورود
                        </button>
                        <button onclick="showPage('register')" class="bg-white bg-opacity-20 px-4 py-2 rounded-lg hover:bg-opacity-30 transition-all">
                            ثبت نام
                        </button>
                    </div>
                    <div id="userMenu" class="hidden">
                        <button class="bg-white bg-opacity-20 px-4 py-2 rounded-lg hover:bg-opacity-30 transition-all">
                            <span id="userName">کاربر</span> 👤
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Home Page -->
    <div id="homePage" class="page active">
        <main class="container mx-auto px-4 py-8">
            <!-- Dashboard Stats -->
            <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
                <div class="bg-gray-800 rounded-xl p-6 text-center">
                    <div class="text-3xl mb-2">🌐</div>
                    <h3 class="text-lg font-semibold mb-1">اتصال فعال</h3>
                    <p class="text-green-400 font-bold">متصل</p>
                </div>
                <div class="bg-gray-800 rounded-xl p-6 text-center">
                    <div class="text-3xl mb-2">📊</div>
                    <h3 class="text-lg font-semibold mb-1">مصرف امروز</h3>
                    <p class="text-blue-400 font-bold">2.3 GB</p>
                </div>
                <div class="bg-gray-800 rounded-xl p-6 text-center">
                    <div class="text-3xl mb-2">⏱️</div>
                    <h3 class="text-lg font-semibold mb-1">زمان باقیمانده</h3>
                    <p class="text-yellow-400 font-bold">15 روز</p>
                </div>
                <div class="bg-gray-800 rounded-xl p-6 text-center">
                    <div class="text-3xl mb-2">🚀</div>
                    <h3 class="text-lg font-semibold mb-1">سرعت</h3>
                    <p class="text-purple-400 font-bold">45 Mbps</p>
                </div>
            </div>

            <!-- VPN Packages -->
            <section class="mb-12">
                <h2 class="text-3xl font-bold text-center mb-8">پکیج‌های VPN</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <!-- Basic Package -->
                    <div class="bg-gray-800 rounded-xl p-6 card-hover border border-gray-700">
                        <div class="text-center mb-6">
                            <h3 class="text-xl font-bold mb-2">پکیج پایه</h3>
                            <div class="text-4xl font-bold text-blue-400 mb-2">50,000 تومان</div>
                            <p class="text-gray-400">ماهانه</p>
                        </div>
                        <ul class="space-y-3 mb-6">
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                حجم 30 گیگابایت
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                5 دستگاه همزمان
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                سرورهای ایران و ترکیه
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                پشتیبانی 24/7
                            </li>
                        </ul>
                        <button onclick="addToCart('basic', 50000, '30GB')" class="w-full bg-blue-600 hover:bg-blue-700 py-3 rounded-lg font-semibold transition-all">
                            افزودن به سبد خرید
                        </button>
                    </div>

                    <!-- Premium Package -->
                    <div class="bg-gray-800 rounded-xl p-6 card-hover border-2 border-purple-500 relative">
                        <div class="absolute -top-3 left-1/2 transform -translate-x-1/2">
                            <span class="bg-purple-500 text-white px-4 py-1 rounded-full text-sm font-semibold">محبوب</span>
                        </div>
                        <div class="text-center mb-6">
                            <h3 class="text-xl font-bold mb-2">پکیج پریمیوم</h3>
                            <div class="text-4xl font-bold text-purple-400 mb-2">120,000 تومان</div>
                            <p class="text-gray-400">ماهانه</p>
                        </div>
                        <ul class="space-y-3 mb-6">
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                حجم 100 گیگابایت
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                10 دستگاه همزمان
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                تمام سرورهای جهان
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                پشتیبانی اولویت‌دار
                            </li>
                        </ul>
                        <button onclick="addToCart('premium', 120000, '100GB')" class="w-full bg-purple-600 hover:bg-purple-700 py-3 rounded-lg font-semibold transition-all">
                            افزودن به سبد خرید
                        </button>
                    </div>

                    <!-- Ultimate Package -->
                    <div class="bg-gray-800 rounded-xl p-6 card-hover border border-gray-700">
                        <div class="text-center mb-6">
                            <h3 class="text-xl font-bold mb-2">پکیج نامحدود</h3>
                            <div class="text-4xl font-bold text-gold-400 mb-2">200,000 تومان</div>
                            <p class="text-gray-400">ماهانه</p>
                        </div>
                        <ul class="space-y-3 mb-6">
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                حجم نامحدود
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                دستگاه نامحدود
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                تمام سرورها + اختصاصی
                            </li>
                            <li class="flex items-center">
                                <span class="text-green-400 ml-2">✓</span>
                                مدیر اختصاصی
                            </li>
                        </ul>
                        <button onclick="addToCart('ultimate', 200000, 'نامحدود')" class="w-full bg-yellow-600 hover:bg-yellow-700 py-3 rounded-lg font-semibold transition-all">
                            افزودن به سبد خرید
                        </button>
                    </div>
                </div>
            </section>

            <!-- Server Status -->
            <section class="mb-12">
                <h2 class="text-2xl font-bold mb-6">وضعیت سرورها</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
                    <div class="bg-gray-800 rounded-lg p-4 flex items-center justify-between">
                        <div>
                            <h4 class="font-semibold">ایران (تهران)</h4>
                            <p class="text-sm text-gray-400">Ping: 12ms</p>
                        </div>
                        <div class="w-3 h-3 bg-green-400 rounded-full pulse-animation"></div>
                    </div>
                    <div class="bg-gray-800 rounded-lg p-4 flex items-center justify-between">
                        <div>
                            <h4 class="font-semibold">ترکیه (استانبول)</h4>
                            <p class="text-sm text-gray-400">Ping: 45ms</p>
                        </div>
                        <div class="w-3 h-3 bg-green-400 rounded-full pulse-animation"></div>
                    </div>
                    <div class="bg-gray-800 rounded-lg p-4 flex items-center justify-between">
                        <div>
                            <h4 class="font-semibold">آلمان (فرانکفورت)</h4>
                            <p class="text-sm text-gray-400">Ping: 78ms</p>
                        </div>
                        <div class="w-3 h-3 bg-yellow-400 rounded-full pulse-animation"></div>
                    </div>
                    <div class="bg-gray-800 rounded-lg p-4 flex items-center justify-between">
                        <div>
                            <h4 class="font-semibold">آمریکا (نیویورک)</h4>
                            <p class="text-sm text-gray-400">Ping: 156ms</p>
                        </div>
                        <div class="w-3 h-3 bg-green-400 rounded-full pulse-animation"></div>
                    </div>
                </div>
            </section>
        </main>
    </div>

    <!-- Register Page -->
    <div id="registerPage" class="page">
        <div class="min-h-screen flex items-center justify-center py-12 px-4">
            <div class="max-w-md w-full">
                <div class="bg-gray-800 rounded-xl shadow-2xl p-8">
                    <div class="text-center mb-8">
                        <div class="w-16 h-16 bg-purple-600 rounded-full flex items-center justify-center mx-auto mb-4">
                            <span class="text-white font-bold text-2xl">V</span>
                        </div>
                        <h2 class="text-3xl font-bold">ثبت نام</h2>
                        <p class="text-gray-400 mt-2">حساب کاربری جدید ایجاد کنید</p>
                    </div>

                    <form id="registerForm" class="space-y-6">
                        <div>
                            <label class="block text-sm font-medium mb-2">نام و نام خانوادگی</label>
                            <input type="text" id="fullName" required class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" placeholder="نام کامل خود را وارد کنید">
                        </div>

                        <div>
                            <label class="block text-sm font-medium mb-2">شماره موبایل</label>
                            <input type="tel" id="phone" required class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" placeholder="09123456789">
                        </div>

                        <div>
                            <label class="block text-sm font-medium mb-2">ایمیل</label>
                            <input type="email" id="email" required class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" placeholder="example@email.com">
                        </div>

                        <div>
                            <label class="block text-sm font-medium mb-2">رمز عبور</label>
                            <input type="password" id="password" required class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" placeholder="حداقل 8 کاراکتر">
                        </div>

                        <div>
                            <label class="block text-sm font-medium mb-2">تکرار رمز عبور</label>
                            <input type="password" id="confirmPassword" required class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" placeholder="رمز عبور را مجدداً وارد کنید">
                        </div>

                        <div class="flex items-center">
                            <input type="checkbox" id="terms" required class="ml-2 w-4 h-4 text-purple-600 bg-gray-700 border-gray-600 rounded focus:ring-purple-500">
                            <label for="terms" class="text-sm text-gray-300">
                                با <a href="#" class="text-purple-400 hover:text-purple-300">قوانین و مقررات</a> موافقم
                            </label>
                        </div>

                        <button type="submit" class="w-full bg-purple-600 hover:bg-purple-700 py-4 rounded-lg font-semibold transition-all transform hover:scale-105">
                            ثبت نام
                        </button>
                    </form>

                    <div class="mt-6 text-center">
                        <p class="text-gray-400">
                            قبلاً حساب دارید؟
                            <button onclick="showPage('login')" class="text-purple-400 hover:text-purple-300 font-semibold">
                                وارد شوید
                            </button>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Login Page -->
    <div id="loginPage" class="page">
        <div class="min-h-screen flex items-center justify-center py-12 px-4">
            <div class="max-w-md w-full">
                <div class="bg-gray-800 rounded-xl shadow-2xl p-8">
                    <div class="text-center mb-8">
                        <div class="w-16 h-16 bg-purple-600 rounded-full flex items-center justify-center mx-auto mb-4">
                            <span class="text-white font-bold text-2xl">V</span>
                        </div>
                        <h2 class="text-3xl font-bold">ورود</h2>
                        <p class="text-gray-400 mt-2">به حساب کاربری خود وارد شوید</p>
                    </div>

                    <form id="loginForm" class="space-y-6">
                        <div>
                            <label class="block text-sm font-medium mb-2">ایمیل یا شماره موبایل</label>
                            <input type="text" id="loginEmail" required class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" placeholder="ایمیل یا شماره موبایل">
                        </div>

                        <div>
                            <label class="block text-sm font-medium mb-2">رمز عبور</label>
                            <input type="password" id="loginPassword" required class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" placeholder="رمز عبور">
                        </div>

                        <div class="flex items-center justify-between">
                            <label class="flex items-center">
                                <input type="checkbox" class="ml-2 w-4 h-4 text-purple-600 bg-gray-700 border-gray-600 rounded focus:ring-purple-500">
                                <span class="text-sm text-gray-300">مرا به خاطر بسپار</span>
                            </label>
                            <a href="#" class="text-sm text-purple-400 hover:text-purple-300">فراموشی رمز عبور؟</a>
                        </div>

                        <button type="submit" class="w-full bg-purple-600 hover:bg-purple-700 py-4 rounded-lg font-semibold transition-all transform hover:scale-105">
                            ورود
                        </button>
                    </form>

                    <div class="mt-6 text-center">
                        <p class="text-gray-400">
                            حساب ندارید؟
                            <button onclick="showPage('register')" class="text-purple-400 hover:text-purple-300 font-semibold">
                                ثبت نام کنید
                            </button>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Cart Page -->
    <div id="cartPage" class="page">
        <div class="container mx-auto px-4 py-8">
            <div class="max-w-4xl mx-auto">
                <div class="flex items-center mb-8">
                    <button onclick="showPage('home')" class="bg-gray-700 hover:bg-gray-600 p-2 rounded-lg ml-4 transition-all">
                        ← بازگشت
                    </button>
                    <h1 class="text-3xl font-bold">سبد خرید</h1>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    <!-- Cart Items -->
                    <div class="lg:col-span-2">
                        <div class="bg-gray-800 rounded-xl p-6">
                            <h2 class="text-xl font-bold mb-6">آیتم‌های سبد خرید</h2>
                            <div id="cartItemsList" class="space-y-4">
                                <!-- Cart items will be populated here -->
                            </div>
                        </div>
                    </div>

                    <!-- Order Summary -->
                    <div class="lg:col-span-1">
                        <div class="bg-gray-800 rounded-xl p-6 sticky top-4">
                            <h3 class="text-xl font-bold mb-6">خلاصه سفارش</h3>

                            <div class="space-y-4 mb-6">
                                <div class="flex justify-between">
                                    <span>جمع کل:</span>
                                    <span id="subtotal">0 تومان</span>
                                </div>
                                <div class="flex justify-between">
                                    <span>تخفیف:</span>
                                    <span class="text-green-400" id="discountAmount">0 تومان</span>
                                </div>
                                <div class="border-t border-gray-700 pt-4">
                                    <div class="flex justify-between text-xl font-bold">
                                        <span>مبلغ نهایی:</span>
                                        <span id="finalTotal" class="text-green-400">0 تومان</span>
                                    </div>
                                </div>
                            </div>

                            <div class="space-y-3">
                                <input type="text" id="discountCode" placeholder="کد تخفیف" class="w-full p-3 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                <button onclick="applyDiscount()" class="w-full bg-gray-600 hover:bg-gray-500 py-2 rounded-lg transition-all">
                                    اعمال کد تخفیف
                                </button>
                            </div>

                            <button onclick="proceedToPayment()" class="w-full mt-6 bg-green-600 hover:bg-green-700 py-4 rounded-lg font-semibold transition-all transform hover:scale-105">
                                ادامه پرداخت
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Payment Page -->
    <div id="paymentPage" class="page">
        <div class="container mx-auto px-4 py-8">
            <div class="max-w-4xl mx-auto">
                <!-- Header -->
                <div class="flex items-center mb-8">
                    <button onclick="showPage('cart')" class="bg-gray-700 hover:bg-gray-600 p-2 rounded-lg ml-4 transition-all">
                        ← بازگشت به سبد خرید
                    </button>
                    <h1 class="text-3xl font-bold">پرداخت</h1>
                </div>

                <!-- Progress Steps -->
                <div class="flex items-center justify-center mb-8">
                    <div class="flex items-center space-x-4 space-x-reverse">
                        <div class="flex items-center">
                            <div class="w-8 h-8 bg-green-500 rounded-full flex items-center justify-center text-white font-bold">✓</div>
                            <span class="mr-2 text-green-400">سبد خرید</span>
                        </div>
                        <div class="w-16 h-1 bg-green-500"></div>
                        <div class="flex items-center">
                            <div class="w-8 h-8 bg-purple-500 rounded-full flex items-center justify-center text-white font-bold">2</div>
                            <span class="mr-2 text-purple-400">پرداخت</span>
                        </div>
                        <div class="w-16 h-1 bg-gray-600"></div>
                        <div class="flex items-center">
                            <div class="w-8 h-8 bg-gray-600 rounded-full flex items-center justify-center text-white font-bold">3</div>
                            <span class="mr-2 text-gray-400">تکمیل</span>
                        </div>
                    </div>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    <!-- Payment Form -->
                    <div class="lg:col-span-2 space-y-6">
                        <!-- Payment Methods -->
                        <div class="bg-gray-800 rounded-xl p-6">
                            <h2 class="text-xl font-bold mb-6">روش پرداخت</h2>
                            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                                <div class="payment-method border-2 border-gray-600 rounded-lg p-4 cursor-pointer" onclick="selectPaymentMethod('card')">
                                    <div class="text-center">
                                        <div class="text-3xl mb-2">💳</div>
                                        <h3 class="font-semibold">کارت بانکی</h3>
                                        <p class="text-sm text-gray-400">ویزا، مسترکارت</p>
                                    </div>
                                </div>
                                <div class="payment-method border-2 border-gray-600 rounded-lg p-4 cursor-pointer" onclick="selectPaymentMethod('wallet')">
                                    <div class="text-center">
                                        <div class="text-3xl mb-2">💰</div>
                                        <h3 class="font-semibold">کیف پول</h3>
                                        <p class="text-sm text-gray-400">پی‌پال، اسکریل</p>
                                    </div>
                                </div>
                                <div class="payment-method border-2 border-gray-600 rounded-lg p-4 cursor-pointer" onclick="selectPaymentMethod('crypto')">
                                    <div class="text-center">
                                        <div class="text-3xl mb-2">₿</div>
                                        <h3 class="font-semibold">ارز دیجیتال</h3>
                                        <p class="text-sm text-gray-400">بیت کوین، اتریوم</p>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Card Payment Form -->
                        <div id="cardForm" class="bg-gray-800 rounded-xl p-6">
                            <h3 class="text-lg font-bold mb-6">اطلاعات کارت</h3>
                            <form class="space-y-4">
                                <div>
                                    <label class="block text-sm font-medium mb-2">شماره کارت</label>
                                    <input type="text" id="cardNumber" placeholder="1234-5678-9012-3456" class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" maxlength="19">
                                </div>
                                <div class="grid grid-cols-2 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium mb-2">تاریخ انقضا</label>
                                        <input type="text" id="expiryDate" placeholder="MM/YY" class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" maxlength="5">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium mb-2">CVV</label>
                                        <input type="text" id="cvv" placeholder="123" class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none" maxlength="4">
                                    </div>
                                </div>
                                <div>
                                    <label class="block text-sm font-medium mb-2">نام دارنده کارت</label>
                                    <input type="text" id="cardHolder" placeholder="نام و نام خانوادگی" class="form-input w-full p-4 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                </div>
                            </form>
                        </div>

                        <!-- Billing Address -->
                        <div class="bg-gray-800 rounded-xl p-6">
                            <h3 class="text-lg font-bold mb-6">آدرس صورتحساب</h3>
                            <form class="space-y-4">
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium mb-2">نام</label>
                                        <input type="text" class="form-input w-full p-3 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium mb-2">نام خانوادگی</label>
                                        <input type="text" class="form-input w-full p-3 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                    </div>
                                </div>
                                <div>
                                    <label class="block text-sm font-medium mb-2">آدرس</label>
                                    <input type="text" class="form-input w-full p-3 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                </div>
                                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium mb-2">شهر</label>
                                        <input type="text" class="form-input w-full p-3 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium mb-2">استان</label>
                                        <select class="form-input w-full p-3 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                            <option>تهران</option>
                                            <option>اصفهان</option>
                                            <option>شیراز</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium mb-2">کد پستی</label>
                                        <input type="text" class="form-input w-full p-3 bg-gray-700 rounded-lg border border-gray-600 focus:border-purple-500 focus:outline-none">
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>

                    <!-- Order Summary -->
                    <div class="lg:col-span-1">
                        <div class="bg-gray-800 rounded-xl p-6 sticky top-4">
                            <h3 class="text-xl font-bold mb-6">خلاصه سفارش</h3>

                            <!-- Order Items -->
                            <div id="paymentOrderItems" class="space-y-3 mb-6">
                                <!-- Items will be populated here -->
                            </div>

                            <div class="border-t border-gray-700 pt-4 space-y-3">
                                <div class="flex justify-between">
                                    <span>جمع کل:</span>
                                    <span id="paymentSubtotal">0 تومان</span>
                                </div>
                                <div class="flex justify-between">
                                    <span>تخفیف:</span>
                                    <span class="text-green-400" id="paymentDiscount">0 تومان</span>
                                </div>
                                <div class="flex justify-between">
                                    <span>مالیات:</span>
                                    <span id="paymentTax">0 تومان</span>
                                </div>
                                <div class="border-t border-gray-700 pt-3">
                                    <div class="flex justify-between text-xl font-bold">
                                        <span>مبلغ نهایی:</span>
                                        <span id="paymentFinalAmount" class="text-green-400">0 تومان</span>
                                    </div>
                                </div>
                            </div>

                            <!-- Security Info -->
                            <div class="mt-6 p-4 bg-gray-700 rounded-lg">
                                <div class="flex items-center mb-2">
                                    <span class="text-green-400 ml-2">🔒</span>
                                    <span class="text-sm font-semibold">پرداخت امن</span>
                                </div>
                                <p class="text-xs text-gray-400">اطلاعات شما با رمزگذاری SSL محافظت می‌شود</p>
                            </div>

                            <button onclick="processPayment()" class="w-full mt-6 bg-green-600 hover:bg-green-700 py-4 rounded-lg font-semibold transition-all transform hover:scale-105">
                                پرداخت نهایی
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Success Modal -->
    <div id="successModal" class="fixed inset-0 bg-black bg-opacity-50 hidden z-50">
        <div class="flex items-center justify-center min-h-screen p-4">
            <div class="bg-gray-800 rounded-xl p-8 w-full max-w-md text-center">
                <div class="text-6xl mb-4">✅</div>
                <h3 class="text-2xl font-bold mb-4 text-green-400">عملیات موفق!</h3>
                <p id="successMessage" class="text-gray-300 mb-6">عملیات با موفقیت انجام شد.</p>
                <button onclick="closeSuccess()" class="bg-purple-600 hover:bg-purple-700 px-6 py-3 rounded-lg font-semibold transition-all">
                    بازگشت به پنل
                </button>
            </div>
        </div>
    </div>

    <script>
        let cart = [];
        let totalAmount = 0;
        let discountAmount = 0;
        let currentUser = null;
        let selectedPaymentMethod = 'card';

        // Page Navigation
        function showPage(pageId) {
            // Hide all pages
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });

            // Show selected page
            document.getElementById(pageId + 'Page').classList.add('active');

            // Update specific page content
            if (pageId === 'cart') {
                updateCartPage();
            } else if (pageId === 'payment') {
                updatePaymentPage();
            }
        }

        // Cart Functions
        function addToCart(packageType, price, volume) {
            const packageNames = {
                'basic': 'پکیج پایه',
                'premium': 'پکیج پریمیوم',
                'ultimate': 'پکیج نامحدود'
            };

            const item = {
                id: Date.now(),
                name: packageNames[packageType],
                price: price,
                volume: volume,
                type: packageType
            };

            cart.push(item);
            updateCartUI();

            // Show success message
            const button = event.target;
            const originalText = button.textContent;
            button.textContent = '✓ اضافه شد';
            button.classList.add('bg-green-600');

            setTimeout(() => {
                button.textContent = originalText;
                button.classList.remove('bg-green-600');
            }, 1500);
        }

        function updateCartUI() {
            const cartCount = document.getElementById('cartCount');
            cartCount.textContent = cart.length;

            totalAmount = cart.reduce((sum, item) => sum + item.price, 0);
            updateAllPriceDisplays();
        }

        function updateAllPriceDisplays() {
            const finalAmount = totalAmount - discountAmount;
            const tax = Math.round(finalAmount * 0.09); // 9% tax
            const finalWithTax = finalAmount + tax;

            // Update cart page
            const subtotalEl = document.getElementById('subtotal');
            const discountEl = document.getElementById('discountAmount');
            const finalTotalEl = document.getElementById('finalTotal');

            if (subtotalEl) subtotalEl.textContent = totalAmount.toLocaleString() + ' تومان';
            if (discountEl) discountEl.textContent = discountAmount.toLocaleString() + ' تومان';
            if (finalTotalEl) finalTotalEl.textContent = finalAmount.toLocaleString() + ' تومان';

            // Update payment page
            const paymentSubtotal = document.getElementById('paymentSubtotal');
            const paymentDiscount = document.getElementById('paymentDiscount');
            const paymentTax = document.getElementById('paymentTax');
            const paymentFinalAmount = document.getElementById('paymentFinalAmount');

            if (paymentSubtotal) paymentSubtotal.textContent = totalAmount.toLocaleString() + ' تومان';
            if (paymentDiscount) paymentDiscount.textContent = discountAmount.toLocaleString() + ' تومان';
            if (paymentTax) paymentTax.textContent = tax.toLocaleString() + ' تومان';
            if (paymentFinalAmount) paymentFinalAmount.textContent = finalWithTax.toLocaleString() + ' تومان';
        }

        function updateCartPage() {
            const cartItemsList = document.getElementById('cartItemsList');

            if (cart.length === 0) {
                cartItemsList.innerHTML = `
                    <div class="text-center py-12">
                        <div class="text-6xl mb-4">🛒</div>
                        <h3 class="text-xl font-semibold mb-2">سبد خرید خالی است</h3>
                        <p class="text-gray-400 mb-6">هنوز هیچ پکیجی انتخاب نکرده‌اید</p>
                        <button onclick="showPage('home')" class="bg-purple-600 hover:bg-purple-700 px-6 py-3 rounded-lg font-semibold transition-all">
                            مشاهده پکیج‌ها
                        </button>
                    </div>
                `;
            } else {
                cartItemsList.innerHTML = cart.map(item => `
                    <div class="flex items-center justify-between p-4 bg-gray-700 rounded-lg">
                        <div class="flex items-center space-x-4 space-x-reverse">
                            <div class="w-12 h-12 bg-purple-600 rounded-lg flex items-center justify-center">
                                <span class="text-white font-bold">V</span>
                            </div>
                            <div>
                                <h4 class="font-semibold">${item.name}</h4>
                                <p class="text-sm text-gray-400">حجم: ${item.volume}</p>
                            </div>
                        </div>
                        <div class="text-left">
                            <p class="font-semibold text-lg">${item.price.toLocaleString()} تومان</p>
                            <button onclick="removeFromCart(${item.id})" class="text-red-400 hover:text-red-300 text-sm mt-1">
                                حذف از سبد
                            </button>
                        </div>
                    </div>
                `).join('');
            }

            updateAllPriceDisplays();
        }

        function updatePaymentPage() {
            const paymentOrderItems = document.getElementById('paymentOrderItems');

            if (cart.length > 0) {
                paymentOrderItems.innerHTML = cart.map(item => `
                    <div class="flex justify-between items-center py-2">
                        <div>
                            <h4 class="font-medium text-sm">${item.name}</h4>
                            <p class="text-xs text-gray-400">${item.volume}</p>
                        </div>
                        <span class="font-semibold text-sm">${item.price.toLocaleString()} تومان</span>
                    </div>
                `).join('');
            }

            updateAllPriceDisplays();
        }

        function removeFromCart(itemId) {
            cart = cart.filter(item => item.id !== itemId);
            updateCartPage();
        }

        function applyDiscount() {
            const discountCode = document.getElementById('discountCode').value.trim();
            const validCodes = {
                'WELCOME10': 0.1,
                'SAVE20': 0.2,
                'VIP30': 0.3
            };

            if (validCodes[discountCode]) {
                discountAmount = Math.round(totalAmount * validCodes[discountCode]);
                updateAllPriceDisplays();

                // Show success message
                const button = event.target;
                const originalText = button.textContent;
                button.textContent = '✓ اعمال شد';
                button.classList.add('bg-green-600');

                setTimeout(() => {
                    button.textContent = originalText;
                    button.classList.remove('bg-green-600');
                }, 2000);
            } else {
                alert('کد تخفیف نامعتبر است');
            }
        }

        // Payment Functions
        function proceedToPayment() {
            if (cart.length === 0) {
                alert('سبد خرید خالی است!');
                return;
            }
            showPage('payment');
        }

        function selectPaymentMethod(method) {
            selectedPaymentMethod = method;

            // Update UI
            document.querySelectorAll('.payment-method').forEach(el => {
                el.classList.remove('selected');
            });
            event.currentTarget.classList.add('selected');

            // Show/hide relevant forms
            const cardForm = document.getElementById('cardForm');
            if (method === 'card') {
                cardForm.style.display = 'block';
            } else {
                cardForm.style.display = 'none';
            }
        }

        function processPayment() {
            // Validate form based on payment method
            if (selectedPaymentMethod === 'card') {
                const cardNumber = document.getElementById('cardNumber').value;
                const expiryDate = document.getElementById('expiryDate').value;
                const cvv = document.getElementById('cvv').value;
                const cardHolder = document.getElementById('cardHolder').value;

                if (!cardNumber || !expiryDate || !cvv || !cardHolder) {
                    alert('لطفاً تمام فیلدهای کارت را پر کنید');
                    return;
                }
            }

            const button = event.target;
            button.textContent = 'در حال پردازش...';
            button.disabled = true;

            setTimeout(() => {
                showSuccessModal('پرداخت موفق!', 'پکیج شما با موفقیت فعال شد. اطلاعات اتصال به ایمیل شما ارسال شده است.');

                // Reset cart
                cart = [];
                discountAmount = 0;
                updateCartUI();

                // Reset button
                button.textContent = 'پرداخت نهایی';
                button.disabled = false;
            }, 3000);
        }

        // Authentication Functions
        function handleRegister(event) {
            event.preventDefault();

            const fullName = document.getElementById('fullName').value;
            const phone = document.getElementById('phone').value;
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            const terms = document.getElementById('terms').checked;

            // Validation
            if (!terms) {
                alert('لطفاً قوانین و مقررات را بپذیرید');
                return;
            }

            if (password !== confirmPassword) {
                alert('رمز عبور و تکرار آن یکسان نیستند');
                return;
            }

            if (password.length < 8) {
                alert('رمز عبور باید حداقل 8 کاراکتر باشد');
                return;
            }

            // Simulate registration
            const button = event.target.querySelector('button[type="submit"]');
            button.textContent = 'در حال ثبت نام...';
            button.disabled = true;

            setTimeout(() => {
                currentUser = { name: fullName, email: email, phone: phone };
                updateAuthUI();
                showSuccessModal('ثبت نام موفق!', 'حساب کاربری شما با موفقیت ایجاد شد. خوش آمدید!');

                // Reset form
                document.getElementById('registerForm').reset();
                button.textContent = 'ثبت نام';
                button.disabled = false;
            }, 2000);
        }

        function handleLogin(event) {
            event.preventDefault();

            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;

            if (!email || !password) {
                alert('لطفاً تمام فیلدها را پر کنید');
                return;
            }

            // Simulate login
            const button = event.target.querySelector('button[type="submit"]');
            button.textContent = 'در حال ورود...';
            button.disabled = true;

            setTimeout(() => {
                currentUser = { name: 'کاربر محترم', email: email };
                updateAuthUI();
                showSuccessModal('ورود موفق!', 'با موفقیت وارد حساب کاربری خود شدید.');

                // Reset form
                document.getElementById('loginForm').reset();
                button.textContent = 'ورود';
                button.disabled = false;
            }, 2000);
        }

        function updateAuthUI() {
            const authButtons = document.getElementById('authButtons');
            const userMenu = document.getElementById('userMenu');
            const userName = document.getElementById('userName');

            if (currentUser) {
                authButtons.classList.add('hidden');
                userMenu.classList.remove('hidden');
                userName.textContent = currentUser.name;
            } else {
                authButtons.classList.remove('hidden');
                userMenu.classList.add('hidden');
            }
        }

        // Success Modal
        function showSuccessModal(title, message) {
            document.getElementById('successModal').classList.remove('hidden');
            document.querySelector('#successModal h3').textContent = title;
            document.getElementById('successMessage').textContent = message;
        }

        function closeSuccess() {
            document.getElementById('successModal').classList.add('hidden');
            showPage('home');
        }

        // Event Listeners
        document.getElementById('registerForm').addEventListener('submit', handleRegister);
        document.getElementById('loginForm').addEventListener('submit', handleLogin);

        // Format inputs
        document.addEventListener('input', function(e) {
            if (e.target.id === 'cardNumber') {
                let value = e.target.value.replace(/\D/g, '');
                value = value.replace(/(\d{4})(?=\d)/g, '$1-');
                e.target.value = value;
            }

            if (e.target.id === 'expiryDate') {
                let value = e.target.value.replace(/\D/g, '');
                if (value.length >= 2) {
                    value = value.substring(0,2) + '/' + value.substring(2,4);
                }
                e.target.value = value;
            }

            if (e.target.id === 'phone') {
                let value = e.target.value.replace(/\D/g, '');
                if (value.length > 11) {
                    value = value.substring(0, 11);
                }
                e.target.value = value;
            }
        });

        // Initialize
        updateCartUI();
        updateAuthUI();
        selectPaymentMethod('card'); // Set default payment method
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'97a64262665303d0',t:'MTc1NzA4MDg5NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
