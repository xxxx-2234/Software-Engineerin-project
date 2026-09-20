<div dir="rtl" align="right">
وثيقة مواصفات وتصميم النظام البرمجي (SRS Document)
مشروع: متجر الزهور الإلكتروني (Online Flower Shop System)

 الطالبة: بيان أحمد عبد المعطي.                          
 الدكتور:أمجد فهمي 
  

1. المقدمة ونظرة عامة (Introduction & Overview)

يهدف هذا المشروع إلى تحويل عملية شراء وتنسيق الزهور والهدايا من المتاجر التقليدية إلى نظام تجارة إلكترونية متكامل. يوفر النظام تجربة سلسة للعملاء لتصفح المنتجات، وتخصيص باقات الزهور وإرفاق بطاقات التهنئة، وإتمام عمليات الدفع والمتابعة، بالإضافة إلى إدارة كاملة للمتجر والمخزون وعمليات التوصيل.



2. جمع وتحليل المتطلبات (Requirements Analysis)

 أ. المتطلبات الوظيفية (Functional Requirements)
تصف الوظائف المباشرة التي يجب أن يقدمها النظام للمستخدمين:    
إدارة الحسابات: تسجيل حساب جديد للعميل، تسجيل الدخول، وإدارة الملف الشخصي والعناوين.                              
تصفح والبحث عن الزهور:البحث بأسماء الزهور، التصفية حسب المناسبة أو السعر أو اللون.                             
تخصيص الباقات (Customize Bouquet): إمكانية اختيار نوع الزهور، التغليف، وإضافة بطاقة إهداء بنص مخصص.               
إدارة الطلبات والدفع: إضافة المنتجات إلى السلة، اختيار موقع التوصيل، والدفع الإلكتروني المشفر.                        
تتبع حالة الطلب:متابعة مرحلة الطلب (قيد التجهيز، خرج للتوصيل، تم التسليم).                                         
لوحة تحكم الإدارة (Admin Dashboard):إضافة وتعديل المنتجات، متابعة المخزون، وتعيين السائقين للتوصيل.             

ب. المتطلبات غير الوظيفية (Non-Functional Requirements)
تحدد معايير الجودة والأداء للنظام:                            
الأمان (Security):تشفير بيانات المستخدمين وعمليات الدفع باستخدام بروتوكولات HTTPS و SSL.                      
الأداء والسرعة (Performance):استجابة شاشات المتجر خلال أقل من ثانيتين تحت الضغط المعتاد.                       
سهولة الاستخدام (Usability):تصميم واجهات بسيطة وجذابة متوافقة مع جميع أجهزة الموبايل والحاسوب.                    
الموثوقية (Reliability):ضمان عمل النظام بنسبة تشغيل عالية (Availability 99.9%).                                        



3. التحليل والتصميم باستخدام مخططات UML.      

 أ. مخطط حالات الاستخدام (Use Case Diagram)
يوضح الأطراف والوظائف المتاحة لكل طرف داخل المتجر:

```mermaid
graph LR
    subgraph System["Online Flower Shop System"]
        UC1((Browse & Search Flowers))
        UC2((Customize Bouquet & Card))
        UC3((Place Order & Pay))
        UC4((Track Order Status))
        UC5((Manage Products & Inventory))
        UC6((Assign & Update Delivery))
    end

    Customer[Customer] --> UC1
    Customer --> UC2
    Customer --> UC3
    Customer --> UC4

    Driver[Delivery Driver] --> UC4
    Driver --> UC6

    Admin[Admin] --> UC3
    Admin --> UC5
    Admin --> UC6
```

---

ب. مخطط الفئات (Class Diagram)
يوضح الهيكلية البرمجية للفئات والخصائص والعمليات والعلاقات بينها:

```mermaid
classDiagram
    class Product {
        +int flowerID
        +String name
        +double price
        +int stockQuantity
        +getDetails()
        +updateStock()
    }

    class Customer {
        +int customerID
        +String name
        +String email
        +String address
        +register()
        +placeOrder()
    }

    class Order {
        +int orderID
        +Date orderDate
        +double totalAmount
        +String status
        +createOrder()
        +cancelOrder()
    }

    class Payment {
        +int paymentID
        +String method
        +double amount
        +processPayment()
    }

    Customer "1" -- "0..*" Order : places
    Order "1" -- "1..*" Product : contains
    Order "1" -- "1" Payment : requires
```

---

ج. مخطط المكونات والمعمارية (Component Architecture)
يوضح الطبقات البرمجية التي يتكون منها النظام:                                                                                                                                                          

```mermaid
graph TD
    UI[User Interface Layer / App & Web] --> API[Application Logic Layer / Backend]
    API --> PaymentGateway[Payment Gateway API]
    API --> DB[(Database System / MySQL)]
```

---

4. تصميم هيلكية الواجهات (UI/UX Mockups Structure)

يتكون نظام متجر الزهور من الواجهات الرئيسية التالية:
1. الشاشة الرئيسية (Home Page): لعرض العروض الموسمية، والأقسام الأكثر مبيعاً.
2. شاشة تخصيص الباقة (Customization Screen):واجهة تفاعلية تمكّن العميل من تحديد أنواع الزهور والألوان وكتابة كرت الإهداء.
3. شاشة سلة التسوق والدفع (Checkout Screen):لاستعراض المشتريات وتحديد موقع الاستلام ووسيلة الدفع.
4. لوحة تحكم الإدارة (Dashboard): شاشة مخصصة للمدير لإدارة المنتجات والطلبات والتقارير.</div>



