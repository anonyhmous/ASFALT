# دليل أكواد ASPHALT V5

كل ملف Kotlin موجود منفصلًا في مساره داخل `app/src/main/java/com/example/`، ولا توجد أكواد مدمجة في ملف واحد.

## الملفات الأساسية ووظيفة كل واحد

| المسار | الوظيفة |
|---|---|
| `MainActivity.kt` | نقطة تشغيل التطبيق وإدارة التنقل بين الصفحات. |
| `AytosApplication.kt` | تهيئة خدمات التطبيق والمستودع المشترك. |
| `ui/MainViewModel.kt` | يربط الواجهة بالبيانات والإعدادات وحالة القارئ. |
| `engine/AytosCardParser.kt` | يحلل النص المقروء من كروت الرحلات ويستخرج السعر والمسافات. |
| `engine/AytosOcrEngine.kt` | يحول لقطة الشاشة المحلية إلى نص باستخدام OCR على الجهاز. |
| `engine/AytosJudgmentEngine.kt` | ينفذ قواعد الحساب ويصدر الحكم واقتراح التفاوض. |
| `service/AytosAccessibilityService.kt` | يراقب واجهات التطبيقات المدعومة للقراءة فقط. |
| `service/AytosOverlayManager.kt` | يدير كارت الحكم العائم. |
| `service/AytosPriceTagsOverlay.kt` | يرسم علامات السعر الصغيرة فوق عروض التفاوض. |
| `service/AytosForegroundService.kt` | يحافظ على خدمة القراءة ويعرض إشعار الحالة. |
| `data/AytosRepository.kt` | يجمع عمليات البيانات والحساب والتاريخ. |
| `data/AytosPreferences.kt` | يحفظ إعدادات السائق والثيم ووضع المسافة. |
| `data/AytosDatabase.kt` | قاعدة بيانات Room الأساسية. |
| `data/HistoryAndReportDb.kt` | بيانات سجل الرحلات والتقارير. |
| `data/ZoneDb.kt` | تخزين المناطق المفضلة والمتجنبة. |
| `model/OrderAndJudgment.kt` | نماذج الرحلات وقواعد السائق ونتيجة الحكم. |
| `model/EngineAndVerdict.kt` | أنواع المحرك والدفع والمسافة والحكم. |
| `ui/theme/Color.kt` | لوحة الألوان ووضع النهار والليل. |
| `ui/theme/Theme.kt` | يطبق ألوان الثيم على واجهات Compose. |
| `ui/theme/Type.kt` | إعدادات الخطوط والطباعة. |
| `ui/screens/HomeScreen.kt` | الصفحة الرئيسية. |
| `ui/screens/RulesScreen.kt` | إعدادات قواعد الحساب ووضع المسافة. |
| `ui/screens/ZonesScreen.kt` | إدارة المناطق. |
| `ui/screens/TripAnalysisScreen.kt` | التحليل التفصيلي للرحلة. |
| `ui/screens/MoreScreen.kt` | الأدوات والمعلومات الإضافية. |
| `ui/screens/OnboardingScreen.kt` | شاشة التعريف الأولى. |
| `ui/screens/SetupWizardScreen.kt` | خطوات تفعيل الصلاحيات والخدمات. |
| `ui/components/FloatingJudgmentOverlayContent.kt` | محتوى كارت الحكم الظاهر فوق التطبيقات. |
| `ui/components/SimulatorDialog.kt` | تجربة الحساب ببيانات اختبار. |
| `ui/components/CommonComponents.kt` | مكونات الواجهة المشتركة. |

## وضع المسافة

- `TRIP_ONLY`: يحسب سعر الكيلومتر على مسافة الرحلة من الراكب إلى الوجهة فقط.
- `FULL_DISTANCE`: يحسب على مسافة الاستلام من السائق إلى الراكب مضافًا إليها مسافة الرحلة. هذا الوضع لا يصدر سعرًا/حكمًا نهائيًا إذا لم تُقرأ إحدى المسافتين؛ يعرض انتظار التفاصيل بدل تخمين صفر.
- الاختيار محفوظ في تفضيلات التطبيق ويستمر بعد إغلاقه.

## ملاحظات سلامة

- تم الإبقاء على `applicationId` الأصلي عمدًا لتفادي تغيير هوية التطبيق المثبتة أو فصل بياناته.
- أسماء الكلاسات الداخلية القديمة لم تتغير لتقليل مخاطر كسر الاستدعاءات.
- لم يتم تضمين أي GitHub token أو كلمة مرور في المشروع.
- هذا الدليل يشرح مسؤوليات الملفات؛ لا يعني أن كل ملف تم اختباره على هاتف فعلي.
