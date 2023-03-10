## محتوى الملف 
- ما هو (prisma)؟
- لماذا نستخدم (prisma)
- استخدام حالات
- العمارة النظيفة والطبقات (Clean and layered architecture)
- العلاقات 
- أنواع العلاقات
- اوامر prisma



##  ما هو (prisma)

تحل Prisma محل ORMs التقليدية وتبسط مهام سير عمل قاعدة البيانات:

1 - الوصول: الوصول الآمن إلى قاعدة البيانات من خلال عميل Prisma الذي تم إنشاؤه تلقائيًا (في JavaScript ، TypeScript ، Go)

2 - الترحيل: نمذجة البيانات التصريحية وعمليات الترحيل (اختياري)

3 - الإدارة: إدارة البيانات المرئية باستخدام Prisma Admin

#### يتم استخدامه لبناء واجهات برمجة تطبيقات GraphQL و REST و gRPC وغير ذلك الكثير. يدعم Prisma حاليًا MySQL و PostgreSQL و MongoDB.

ال Prisma مفتوحة المصدر ويمكن استخدامه كمكون مستقل للبنية التحتية مستضاف على مزود السحابة المفضل لديك. Prisma Cloud هو تطبيق (يستخدم من خلال واجهة CLI والويب) يوفر أدوات وخدمات حول Prisma. عند استخدام Prisma ، يكون استخدام Prisma Cloud اختياريًا.

 الهدف من Prisma Cloud هو تسهيل سير العمل في مشاريع Prisma. إنه يتميز بمستعرض البيانات وسجل النشر (قريبًا مع التراجع التلقائي) وخيارات تعاون الفريق المختلفة بالإضافة إلى تكامل مزود السحابة لتسهيل إعداد وصيانة خوادم Prisma الخاصة بهم.
 
 
 ## لماذا نستخدم  (prisma)

#### بسبب سير عمل قاعدة البيانات البسيط

الهدف العام لـ Prisma هو إزالة التعقيد من مهام سير عمل قاعدة البيانات المشتركة وتبسيط الوصول إلى البيانات في تطبيقاتك:
- الوصول الآمن إلى قاعدة البيانات بفضل عميل Prisma المخصص والمُنشأ تلقائيًا.
- واجهة برمجة تطبيقات بسيطة وفعالة للعمل مع البيانات والمعاملات العلائقية.
- إدارة البيانات المرئية باستخدام Prisma Admin.
- يعمل Prisma على توحيد الوصول إلى قواعد بيانات متعددة في وقت واحد (قريبًا) وبالتالي يقلل بشكل كبير من التعقيد في مهام سير العمل عبر قواعد البيانات.
- نظام بث وأحداث في الوقت الفعلي لقاعدة بياناتك يضمن حصولك على تحديثات لجميع الأحداث المهمة التي تحدث في قاعدة البيانات الخاصة بك.
- عمليات الترحيل التلقائية لقاعدة البيانات (اختيارية) استنادًا إلى نموذج بيانات تعريفي يتم التعبير عنه باستخدام لغة تعريف مخطط GraphQL (SDL).
- مهام سير عمل قاعدة البيانات الأخرى مثل استيراد البيانات وتصديرها والمزيد.

## استخدام حالات

#### يعد Prisma مفيدًا في أي سياق تعمل فيه مع قواعد البيانات.

- بناء خوادم GraphQL

ال Prisma هي الأداة المثالية لبناء خوادم GraphQL. عميل Prisma متوافق مع نظام Apollo البيئي ، ولديه دعم افتراضي لاشتراكات GraphQL وتقسيم الصفحات بنمط الترحيل ،ويوفر أمانًا شاملًا ويأتي مزودًا بمحمل بيانات مدمج لحل مشكلة N + 1.

- بناء واجهات برمجة تطبيقات REST و gRPC

ال Prisma مناسب جدًا لبناء واجهات برمجة تطبيقات REST و gRPC حيث يمكن استخدامها بدلاً من ORMs التقليدية. يوفر العديد من الفوائد مثل أمان النوع وواجهة برمجة تطبيقات حديثة وطرق مرنة لقراءة البيانات العلائقية وكتابتها.

- ال CLIs والنصوص والوظائف بدون خادم وغير ذلك الكثير

يحتوي ال Prisma على واجهة برمجة تطبيقات مرنة للغاية مما يجعله مناسبًا لمجموعة متنوعة من حالات الاستخدام. كلما احتجت إلى التحدث إلى قاعدة بيانات واحدة أو أكثر ، ستساعدك Prisma كثيرًا من خلال تبسيط مهام سير عمل قاعدة البيانات.

## العمارة النظيفة والطبقات (Clean and layered architecture)

عند تطوير خوادم التطبيقات ، يكمن معظم التعقيد في تنفيذ وصول آمن وجيد التنظيم إلى قاعدة البيانات فيما يتعلق بالمزامنة وتحسين الاستعلام / الأداء والأمان. يصبح هذا الأمر أكثر تعقيدًا عند تضمين قواعد بيانات متعددة.

أحد الحلول الشائعة لهذه المشكلة هو إدخال طبقة وصول مخصصة للبيانات (DAL) تلخص تعقيدات الوصول إلى قاعدة البيانات. يتم استهلاك واجهة برمجة تطبيقات DAL بواسطة خادم التطبيق ، مما يسمح لمطوري واجهة برمجة التطبيقات بالتفكير ببساطة في البيانات التي يحتاجون إليها بدلاً من القلق بشأن كيفية استعادتها بأمان وبأداء فعال من قاعدة البيانات.



![image](https://i.imgur.com/SUH6AqW.png)

يضمن استخدام DAL فصلًا واضحًا للمخاوف ، وبالتالي يحسن قابلية الصيانة وإعادة استخدام التعليمات البرمجية الخاصة بك. إن الحصول على نوع من تجريد قاعدة البيانات (سواء كانت مكتبة ORM بسيطة أو مكونًا مستقلًا للبنية التحتية) هو أفضل ممارسة للتطبيقات الأصغر حجمًا وكذلك للتطبيقات التي تعمل على نطاق واسع. إنه يضمن أن خادم التطبيق يمكنه التحدث إلى قاعدة البيانات (قواعد البيانات) الخاصة بك بطريقة آمنة وفعالة.

ال Prisma عبارة عن DAL يتم إنشاؤه تلقائيًا ويتبع نفس مبادئ DAL الرائدة في الصناعة (مثل Twitter's Strato أو TAO على Facebook) بينما لا يزال يمكن الوصول إليه للتطبيقات الأصغر.

يتيح لك Prisma بدء مشروعك بهيكلية نظيفة من البداية ويوفر عليك من كتابة النموذج المعياري المطلوب بخلاف ذلك للصق قاعدة البيانات وخادم التطبيق معًا.



## العلاقات

#### العلاقة هي اتصال بين نموذجين في مخطط Prisma. على سبيل المثال ، هناك علاقة رأس بأطراف بين المستخدم والمنشور لأن مستخدم واحد يمكن أن يكون لديه العديد من منشورات المدونة.

#### يحدد مخطط Prisma التالي علاقة رأس بأطراف بين نموذج User و Post. يتم تمييز الحقول المتضمنة في تحديد العلاقة:

    model User {
      id    Int    @id @default(autoincrement())
      posts Post[]
    }

    model Post {
      id       Int  @id @default(autoincrement())
      author   User @relation(fields: [authorId], references: [id])
      authorId Int // relation scalar field  (used in the `@relation` attribute above)
    }

على مستوى Prisma ، تتكون علاقة المستخدم / المنشور من:

- مجالان للعلاقة: المؤلف والمشاركات. تحدد حقول العلاقة الاتصالات بين النماذج على مستوى Prisma ولا توجد في قاعدة البيانات. تُستخدم هذه الحقول لإنشاء عميل Prisma.
- حقل معرف المؤلف القياسي ، والذي تتم الإشارة إليه بواسطة السمةrelation. هذا الحقل موجود في قاعدة البيانات - إنه المفتاح الخارجي الذي يربط Post والمستخدم.

على مستوى Prisma ، يتم دائمًا تمثيل الاتصال بين نموذجين بحقل علاقة على كل جانب من جوانب العلاقة.

#### قواعد البيانات العلائقية

يحدد الرسم التخطيطي لعلاقة الكيان التالي نفس علاقة one-to-many بين جدول المستخدم و Post في قاعدة بيانات علائقية:

![image](https://www.prisma.io/docs/static/e83a6a5933258930b5e6b7bc6f1bf839/e548f/one-to-many.png)

#### في SQL ، يمكنك استخدام مفتاح خارجي لإنشاء علاقة بين جدولين. يتم تخزين المفاتيح الخارجية على جانب واحد من العلاقة. يتكون مثالنا من:

- عمود مفتاح خارجي في جدول النشر يسمى authorId.
- عمود المفتاح الأساسي في جدول المستخدم المسمى id. يشير عمود authorId في جدول Post إلى عمود المعرف في جدول المستخدم.

في مخطط Prisma ، يتم تمثيل علاقة المفتاح الخارجي / المفتاح الأساسي بواسطة السمةrelation في حقل المؤلف:

      author     User        @relation(fields: [authorId], references: [id]) 


## أنواع العلاقات

- ال One-to-one (وتسمى أيضًا علاقة 1-1)
- ال One-to-many (وتسمى أيضًا علاقة 1-n)
- ال Many-to-many (وتسمى أيضًا علاقة m-n)

#### يتضمن مخطط Prisma التالي كل نوع من العلاقات:



ا ![image](https://user-images.githubusercontent.com/92247967/200191773-5b94c20c-99f8-4994-85a5-d7b04be4b598.png)

#### يمثل الرسم التخطيطي لعلاقة الكيان التالي قاعدة البيانات التي تتوافق مع نموذج مخطط Prisma:

![image](https://www.prisma.io/docs/static/80c7aa384ca962faf5be1ee91f89aa7e/e548f/sample-schema.png)

## مجالات العلاقة

- يجب أن تحتوي كل علاقة على حقلي علاقة بالضبط ، واحد في كل نموذج. في حالة العلاقات 1-1 و 1-n ، يلزم وجود حقل عددي للعلاقة إضافي يتم ربطه بأحد حقلي العلاقة في السمةrelation. مقياس العلاقة هذا هو التمثيل المباشر للمفتاح الخارجي في قاعدة البيانات الأساسية.

#### ضع في اعتبارك هذه النماذج:

       model User {
         id      Int      @id @default(autoincrement())
         posts   Post[]
         profile Profile?
       }

       model Profile {
         id     Int  @id @default(autoincrement())
         user   User @relation(fields: [userId], references: [id])
         userId Int  @unique // relation scalar field (used in the `@relation` attribute above)
       }

       model Post {
         id         Int        @id @default(autoincrement())
         author     User       @relation(fields: [authorId], references: [id])
         authorId   Int // relation scalar field  (used in the `@relation` attribute above)
         categories Category[]
       }

       model Category {
         id    Int    @id @default(autoincrement())
         posts Post[]
       }

## اوامر prisma

![Frame 1](https://user-images.githubusercontent.com/92247967/200297230-f8ddf4fb-014f-4343-a6f5-0db55d1bbf01.png)

  
      
 
