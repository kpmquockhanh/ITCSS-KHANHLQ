## ITCSS: ~~Kĩ thuật bảo trì và mở rộng CSS~~(SCALABLE AND MAINTAINABLE CSS ARCHITECTURE)*Bảo trì và mở rộng kiến trúc CSS*
Lubos Kmetko ngày 10 tháng 2 năm 2016 
### Làm thế nào để mở rộng và bảo trì CSS của bạn? Đó là vấn đề quan tâm của mọi nhà phát triển front-end. ITCSS là một câu trả lời.

Năm ngoái khi tôi bắt đầu kế ~~hoặc~~(hoạch) thiết kế lại [HEROized](https://www.heroized.com/) của chúng tôi và thiết kế trang  Xfive.co mới, tôi đã tìm kiếm một ~~kĩ thuật~~(architecture)**kiến trúc** css cái mà có thể cho phép phát triển web và bảo trì sau này một cách dễ dàng.

Thời gian đó [CSS Modules](http://www.sitepoint.com/understanding-css-modules-methodology/) mới đang trong giai đoạn đầu và còn mới mẻ và tôi luôn ~~cho rằng~~(considered) **xem xét** sự tương đồng trong cấu trúc [Atomic Design](http://patternlab.io/) dễ nhân tạo hơn. Sau đó tôi bắt gặp ITCSS của [Harry Roberts’s](https://csswizardry.com/) phát hành tháng 6 2015 của [net magazine](https://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731) và ngay lập tức thích nó bởi sự đơn giản, thực tế trong cách nó tiếp cận css
 ### ITCSS là gì?
 ITCSS viêt tắt của _Inverted Triangle_ CSS và nó giúp bạn tổ chức file css sao cho có thể **giải quyết** tốt hơn những vấn đề đặc biệt của css (không phải lúc nào cũng dễ giải quyết) giống như là  **global namespace, cascade and selectors specificity.**.
ITCSS có thể sử dụng cùng với bộ tiền sử lý hoặc không và nó tương thích với CSS ~~phương pháp luận~~(methodologies) **phương thức**  css như BEM, SMACSS hoặc OOCSS.
Một trong những nguyên tắc chính của ITCSS đó là nó chia css codebase của bạn thành nhiều phần nhỏ (được gọi là các lớp), có dạng hình tam giác ngược:
![inverted triangle](https://other.media/wp-content/uploads/2017/01/itcss_2.png)
Các lớp như sau:
 - Settings - Sử dụng với các tiền xử lý bao gồm phông chữ, định nghĩa màu sắc v.v..
 - Tool - Được sử dụng mixin và các hàm. Quan trọng là ~~không được xuất~~(not to output) **không tạo ra** bất kì css nào trong hai lớp đầu tiên.
 - Generic - cài lại và/hoặc chuẩn hóa style, định nghĩa box-sizing v.v. Đây là lớp đầu tiên thực sự tạo ra css.
 - Elements - Định kiểu cho các phần tử HTML cơ bản (như H1, A, v.v). ~~These come with default styling from the browser so we can redefine them here.~~ **Chúng đi kèm với định dạng mặc định từ trình duyệt để chúng tôi có thể xác định lại chúng ở đây.**
 - Objects - Các selector dựa trên lớp, định nghĩa các mẫu thiết kế chưa được trang trí, ví dụ như đối tượng media từ OOCSS. 
 - Components - các thành phần UI đặc biệt. Đây là nơi đa số công việc diễn ra và thành phần UI của chúng tôi thường bao gồm đối tượng và thành phần.
 - Utilities - các lớp tiện ích và trợ giúp với khả năng ghi đè bất cứ thứ gì đi trước trong hình tam giác trên, ví dụ ~~lớp hỗ trợ ẩn~~ ( hide helper ) **ẩn lớp hỗ trợ**.
Hình tam giác trên cũng cho thấy các style được trình bày bởi các selector được sắp xếp trong kết quả CSS: từ các style chung chung đến các kiểu rõ ràng, từ các selector có độ đặc hiệu thấp đến những kiểu cụ thể hơn (nhưng vẫn không quá cụ thể, không cho phép ID) và từ ảnh hưởng rộng đến ảnh hưởng ít.
![inverted triangle](https://other.media/wp-content/uploads/2017/01/itcss_1.png)
Tổ chức CSS như vậy giúp bạn tránh được những xung đột cụ thể và được trình bày bởi [một biểu đồ đặc hiệu lành mạnh ](https://jonassebastianohlsson.com/specificity-graph/)
 ### Tài liệu
Cập nhật ngày 10/27/2016: Net magazine vừa tái xuất bản bài báo ban đầu từ phiên bản báo tạp chí(xem nguồn phía dưới).
Như thường lệ, vào điểm này tôi sẽ dẫn bạn đến các [trang web ITCSS](https://itcss.io/) để tìm hiểu thêm. Tuy nhiên , chưa có tài liệu mã nguồn mở nào cả .
 ITCSS hiện nãy vẫn còn một phần thuộc sở hữu độc quyền nên nếu bạn muốn hoàn toàn sử dụng nó, bạn nên đọc bài giới thiệu gốc từ net magazine. Tôi không ở đây để phán xét quyết định của tác giả (tôi cảm ơn ông ý vì đã chia sẻ kiến thức), nhưng tôi nghĩ điều này sẽ ngăn cản ITCSS được áp dụng rộng rãi (có thể đây chính là chủ ý của ông ấy).
 > Tính độc quyền một phần của ITCSS ngăn cản việc áp dụng rộng rãi hơn.

Nếu bạn thực sự thích nó thì không nên vì điều này mà bạn ngừng sử dụng nó trong việc bắt đầu dự án. Xem các [vấn đề đặc biệt ](https://www.myfavouritemagazines.co.uk/design/net-magazine-back-issues/)  của net magazine để học các vấn đề cơ bản của ITCSS, và sau đó bạn có thể học từ các nguồn online và qua các ví dụ áp dụng nó trong các dự án thực tế.
### Nguồn
Tôi đã sử dụng ITCSS trong 4 dự án trước đây (bao gồm Xfive.co) và những nguồn dưới đây giúp ~~toou~~ **tôi** hiểu về nó nhiều hơn:
 - [Quản lý dự án CSS lớn với ITCSS](http://www.creativebloq.com/web-design/manage-large-css-projects-itcss-101517528) - giới thiệu ITCSS của Harry Roberts (bài báo gốc được xuất bản từ phiên bản báo tạp chí, mất 1 vài cột ở biểu đồ đặc thù và bộ tiền xử lý)
 - [Quản lý dự án web qui mô lớn với kĩ thuật CSS mới ITCSS](https://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731) - giới thiệu ITCSS và phỏng vấn Harry Roberts
 - [Harry Roberts – Quản lý dự án CSS với ITCSS ](https://www.youtube.com/watch?v=1OKZOV-iLj4) cuộc nói chuyện của Harry tại DaFED and [slide đi kèm](https://speakerdeck.com/dafed/managing-css-projects-with-itcss)
 - [Quản lý dự án CSS lớn với ITCSS](https://www.youtube.com/watch?v=hz76JIU_xB0) - một screencast cho các bài báo.
 - [ITCSS Screencast code](https://github.com/itcss/itcss-netmag) -  mã nguồn từ screencast tại GitHub
 - [Các dự án mẫu ITCSS khác](https://github.com/csswizardry/frcss)
 - Các bài báo tại csswizardry.com và đặc biệt các bài dưới đây:
    - [BEMIT: Quy ước đặt tên BEM mở rộng](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)
    - [Code UI sáng sủa hơn với Namespaces](https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
    - [CSS bất biến](https://csswizardry.com/2015/03/immutable-css/)
    - [Biểu đồ đặc trưng](https://csswizardry.com/2014/10/the-specificity-graph/)
 - [inuitcss](https://github.com/inuitcss/inuitcss) - OOCSS framework dựa trên ITCSS, cải tiến một số chức năng và khái niệm.
 - [Quy ước đặt tên BEMIT](http://www.jamesturneronline.net/blog/bemit-naming-convention.html)
Bạn có thể kiểm tra tại [Chisel](https://github.com/xfiveco/generator-chisel/), bộ sinh Yeoman cho các dự án front-end và WordPress của chúng tôi, nó có hỗ trợ ITCSS.
 ### Kinh nghiệm
Ở đây có một vài suy nghĩ dựa trên kinh nghiệm của tôi với các dự án ITCSS:
 ##### Ít suy nghĩ về đặt tên hay tạo mẫu vị trí 
Bản chất tự tiên của ITCSS, đặc biệt khi kết hợp với  [ quy ước đặt tên BEMIT](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/) cho phép bạn tập trung vài việc giải quyết các thách thức front-end thay vì nghĩ về tên gọi hay mẫu của các vị trí. Đây, file main.css của Xfive.co có dạng thế này:
```css
@import "settings.colors";
@import "settings.global";

@import "tools.mixins";

@import "normalize-scss/normalize.scss";
@import "generic.reset";
@import "generic.box-sizing";
@import "generic.shared";

@import "elements.headings";
@import "elements.hr";
@import "elements.forms";
@import "elements.links";
@import "elements.lists";
@import "elements.page";
@import "elements.quotes";
@import "elements.tables";

@import "objects.animations";
@import "objects.drawer";
@import "objects.list-bare";
@import "objects.media";
@import "objects.layout";
@import "objects.overlays";

@import "components.404";
@import "components.about";
@import "components.archive";
@import "components.avatars";
@import "components.blog-post";
@import "components.buttons";
@import "components.callout";
@import "components.clients";
@import "components.comments";
@import "components.contact";
@import "components.cta";
@import "components.faq";
@import "components.features";
@import "components.footer";
@import "components.forms";
@import "components.header";
@import "components.headings";
@import "components.hero";
@import "components.jobs";
@import "components.legal-nav";
@import "components.main-cta";
@import "components.main-nav";
@import "components.newsletter";
@import "components.page-title";
@import "components.pagination";
@import "components.post-teaser";
@import "components.process";
@import "components.quote-banner";
@import "components.offices";
@import "components.sec-nav";
@import "components.services";
@import "components.share-buttons";
@import "components.social-media";
@import "components.team";
@import "components.testimonials";
@import "components.topbar";
@import "components.reasons";
@import "components.wordpress";
@import "components.work-list";
@import "components.work-detail";

@import "vendor.prism";

@import "trumps.clearfix";
@import "trumps.utilities";

@import "healthcheck";
```
Chú ý: Chúng ta sử dụng [các thư mục tách rời cho mỗi lớp](https://github.com/xfiveco/generator-chisel/tree/master/generators/app/templates/styles/itcss) tự động tải các định dạng thêm mới bằng  [Chisel](https://github.com/xfiveco/generator-chisel/)
 ##### Đối tượng sử dụng lại cho sự phát triển nhanh
 Các đối tượng của ITCSS là ứng cử viên hàng đầu cho việc xây dựng thư viện các thành phần dùng lại được nhằm phát triển front-end nhanh hơn. Các thành phần UI bao gồm các đối tượng chung và các thành phần đặc thù của dự án. Ví dụ, innuitcss là một framework dựa trên ITCSS,chứa  [một nhóm đối tượng](https://github.com/inuitcss/inuitcss/tree/develop/objects) ~~bnhưng chủ~~ **nhưng chỉ**  [một thành phần mẫu](https://github.com/inuitcss/inuitcss/tree/develop/components)
 ##### Hoạt hình *Animations*
 Tôi khuyên bạn nên định nghĩa các hoạt ảnh chung như là các đối tượng, ví dụ như @keyframes o-fade-in trong file _objects.animations.scss

 Các thành phần đặc thù cho hoạt ảnh nên được định nghĩa trong các file thành phần tương ứng, ví dụ @keyframes c-hero-scale trong file _components.hero.scss.
 ##### Sự linh hoạt
 ITCSS rất linh hoạt trong luồng công việc cũng như các công cụ của bạn. Một trong nhưng lập trình viên của chúng tôi đã bày tỏ sự quan tâm về việc ITCSS nó đã đầy đủ như thế nào. Nhưng sự thật là điều đó hoàn toàn phụ thuộc vào bạn - ITCSS không yêu cầu bạn phải có tất cả các lớp (chỉ cái nào cần thôi)

 Do vậy trong 1 cài đặt tối thiểu, bạn có thể chỉ cần 1 vài thành phần với những phần tử mẫu mặc định theo trình duyệt. Tất nhiên là điều này không thiết thực chút nào - một vài cài đặt, đặt lại và/ hay chuẩn hóa CSS được sử dụng bởi hầu hết mọi người vì những lợi ích của chúng.
 ##### Critical CSS 
 ITCSS đóng vai trò tốt với critical CSS do các chỉ số then chốt tam giác ngược. Mô hình dựa trên thành phần cho phép bạn tách UI trên giao diện người dùng thành các thành phần logic nên bạn thậm chí có thể chọn các phần của critical CSS thủ công  (thêm vào đó trong bài viết sắp tới).
 ##### Kích thước file và ~~lập mẫu~~(duplication) *sao chép style*
Nếu có bất kỳ mỗi mối bận tâm nào về kiến trúc như ITCSS hay đơn giản là bất kỳ thành phần nào như là kiến trúc CSS, nó có thể là kết quả của kích thước file. Các thành phần sẽ đóng gói các mẫu và cho phép chúng ta tránh các xung đột CSS và ghi đè, tuy nhiên điều này cũng đồng nghĩa với việc sự lặp lại mẫu có thể thường xuyên xảy ra.

ITCSS dường như không thể cạnh tranh được với [CSS chức năng ](https://blog.colepeters.com/building-and-shipping-functional-css/). Mặt khác,, nếu bạn nhận thấy lặp quá nhiều mẫu trong các thành phần, bạn có thể cân nhắc đến việc chuyển các mẫu đó đến các đối tượng riêng biệt.
### Kết luận 
Bạn sẽ không mắc sai lầm với ITCSS được. Nó là kết quả của kinh nghiệm và rất nhiều năm làm việc của Harry Roberts, một trong những tác giả CSS nổi tiếng nhất trên thế giới. Nếu bạn muốn đào sâu vào mã nguồn 1 chút, bạn sẽ thấy rằng đây là một kiến trúc đơn giản nhưng mô cùng mạnh mẽ, cho phép bạn tạo ra những dự án nhỏ lẫn to với CSS rất dễ mở rộng và bảo trì. Tuy nhiên, đừng quên để mắt đến những cái khác như [CSS modules](https://github.com/css-modules/css-modules) trong lúc rảnh rỗi.
 
 ##### Interested in more ITCSS?
 - [ITCSS: Một năm sau](https://www.xfive.co/blog/itcss-year-after/) - 5 điều nhận ra sau 1 năm với Inverted Triangle CSS.
 - Xem qua [Chisel](https://github.com/xfiveco/generator-chisel), bộ sinh Yeoman cho các dự án front-end và WordPress của chúng tôi, nó có hỗ trợ ITCSS 