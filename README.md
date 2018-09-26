# Design_by_contract

[Source](https://en.m.wikipedia.org/wiki/Design_by_contract "Permalink to Design by contract - Wikipedia")

# Design bằng contract - Wikipedia

![][1]

1 kế hoạch thiết kế bằng contract

*Design bằng contract* (*DbC*), còn được biết là *contract programming*, *programming by contract* và *design-by-contract programming*, là 1 hướng tiếp cận để thiết kế phần mềm. Nó quy định rằng các nhà thiết kế phần mềm nên khai báo các đặc tả interface 1 cách chính quy, tóm lượng và dễ kiểm tra đối với các thành phần phần mềm, nhằm mở rộng các định nghĩa thông thường của các loại dữ liệu trừu tượng  với điều kiện  trước, điều kiện sau và bất biến. Những đặc tả này được gọi là "contract", phù hợp với một ẩn dụ khái niệm với các điều kiện và nghĩa vụ của  các contract công việc.

Cách tiếp cận DbC giả định tất cả các thành phần máy khách gọi một hoạt động trên một thành phần máy chủ sẽ đáp ứng các điều kiện tiên quyết được xác định theo yêu cầu cho hoạt động đó. Trường hợp giả định này được coi là quá rủi ro (như trong máy chủ đa kênh hoặc máy tính phân tán), phương pháp "thiết kế phòng thủ" ngược lại được thực hiện, nghĩa là kiểm tra thành phần máy chủ (trước hoặc trong khi xử lý yêu cầu của khách hàng). đúng, và trả lời với một thông báo lỗi phù hợp nếu không.

## Nội dung

Ý tưởng trung tâm của DbC là một phép ẩn dụ về cách các yếu tố của một hệ thống phần mềm cộng tác với nhau trên cơ sở các nghĩa vụ và lợi ích chung. Ẩn dụ xuất phát từ cuộc sống công việc, nơi “khách hàng” và “nhà cung cấp” đồng ý với “hợp đồng” xác định, ví dụ:
* Nhà cung cấp phải cung cấp một sản phẩm nhất định (nghĩa vụ) và hi vọng khách hàng đã thanh toán phí (lợi ích) của mình.
* Khách hàng phải trả phí (nghĩa vụ) và được quyền nhận sản phẩm (lợi ích).
* Cả hai bên phải đáp ứng các nghĩa vụ nhất định, chẳng hạn như luật và quy định, áp dụng cho tất cả các hợp đồng.


Tương tự, nếu một đoạn chương trình từ một lớp trong lập trình hướng đối tượng cung cấp một chức năng nhất định, nó có thể:

* Mong đợi một điều kiện nhất định được đảm bảo khi nhập vào bởi bất kỳ mô-đun khách hàng nào gọi nó: điều kiện tiên quyết của đoạn ct đó - nghĩa vụ cho khách hàng và lợi ích cho nhà cung cấp (là chính nó), vì nó giải phóng nó khỏi phải xử lý các trường hợp bên ngoài điều kiện tiên quyết.
* Đảm bảo một thuộc tính nhất định khi thoát ra: điều kiện của thường lệ — một nghĩa vụ đối với nhà cung cấp, và rõ ràng là một lợi ích (lợi ích chính của việc gọi thường trình) cho khách hàng.
* Duy trì một tài sản nhất định, giả định về đầu vào và được bảo đảm khi thoát: lớp bất biến.

Hợp đồng này tương đương về mặt ngữ nghĩa với một luật Hoare triple,  hình thức hóa các nghĩa vụ. Điều này có thể được tóm tắt bằng "ba câu hỏi" mà nhà thiết kế phải nhiều lần trả lời trong hợp đồng:

* Hợp đồng kỳ vọng điều gì?
* Bảo đảm hợp đồng điều gì?
* Hợp đồng duy trì điều gì?

Nhiều ngôn ngữ lập trình có cơ sở để đưa ra các xác nhận như thế này. Tuy nhiên, DbC coi các hợp đồng này là rất quan trọng đối với tính chính xác của phần mềm mà chúng phải là một phần của quá trình thiết kế. Trong thực tế, DbC chủ trương viết các xác nhận đầu tiên. Các hợp đồng có thể được viết bằng các chú thích mã, được thi hành bởi một bộ kiểm thử, hoặc cả hai, ngay cả khi không có sự hỗ trợ ngôn ngữ đặc biệt cho các hợp đồng.

Khái niệm về hợp đồng kéo dài xuống mức phương thức / thủ tục; hợp đồng cho mỗi phương pháp thường sẽ chứa các thông tin sau: [_ citation needed_]

* Các giá trị hoặc loại đầu vào được chấp nhận và không được chấp nhận và ý nghĩa của chúng
* Trả lại giá trị hoặc loại và ý nghĩa của chúng
* Lỗi và các giá trị hoặc loại điều kiện ngoại lệ có thể xảy ra và ý nghĩa của chúng
* Tác dụng phụ
* Điều kiện tiên quyết
* Postconditions
* Bất biến
* (hiếm khi hơn) Đảm bảo hiệu suất, ví dụ: cho thời gian hoặc không gian được sử dụng

Các lớp con trong một hệ thống phân cấp thừa kế được phép làm suy yếu các điều kiện tiên quyết (nhưng không tăng cường chúng) và tăng cường các điều kiện và bất biến (nhưng không làm suy yếu chúng). Những quy tắc này gần đúng về phân loại hành vi.

Tất cả các mối quan hệ lớp nằm giữa giữa các lớp khách và các lớp nhà cung cấp. Một lớp khách có nghĩa vụ thực hiện các cuộc gọi đến các tính năng của nhà cung cấp, nơi trạng thái kết quả của nhà cung cấp không bị vi phạm bởi cuộc gọi của khách hàng. Sau đó, nhà cung cấp có nghĩa vụ cung cấp trạng thái trả lại và dữ liệu không vi phạm các yêu cầu của tiểu bang của khách hàng. Ví dụ, bộ đệm dữ liệu của nhà cung cấp có thể yêu cầu dữ liệu đó có trong bộ đệm khi một tính năng xóa được gọi. Sau đó, nhà cung cấp đảm bảo cho khách hàng rằng khi một tính năng xóa kết thúc công việc của nó, mục dữ liệu sẽ thực sự bị xóa khỏi bộ đệm. Các hợp đồng thiết kế khác là các khái niệm về “bất biến lớp”. Lớp bảo đảm bất biến (đối với lớp địa phương) rằng trạng thái của lớp sẽ được duy trì trong các dung sai được chỉ định ở cuối mỗi thực thi tính năng.

Khi sử dụng hợp đồng, nhà cung cấp không nên cố gắng xác minh rằng các điều kiện hợp đồng được thỏa mãn; ý tưởng chung là mã nên "thất bại", với xác minh hợp đồng là mạng lưới an toàn. Tài sản "không cứng" của DbC đơn giản hoá việc gỡ rối hành vi hợp đồng, vì hành vi dự định của từng thói quen được xác định rõ ràng. Điều này phân biệt nó rõ ràng từ một thực hành liên quan được gọi là lập trình phòng thủ, nơi mà các nhà cung cấp chịu trách nhiệm cho việc tìm ra phải làm gì khi một điều kiện tiên quyết bị phá vỡ. Thường xuyên hơn không, nhà cung cấp ném một ngoại lệ để thông báo cho khách hàng rằng điều kiện tiên quyết đã bị phá vỡ, và trong cả hai trường hợp - DbC và lập trình phòng thủ — khách hàng phải tìm ra cách để đáp ứng điều đó. DbC giúp công việc của nhà cung cấp dễ dàng hơn.

Thiết kế theo hợp đồng cũng xác định tiêu chí cho tính chính xác cho một module phần mềm:

* Nếu lớp bất biến và điều kiện tiên quyết là đúng trước khi một nhà cung cấp được gọi bởi một máy khách, thì sự bất biến và điều kiện sau sẽ là đúng sau khi dịch vụ đã được hoàn thành.
* Khi thực hiện lời gọi đến nhà cung cấp, mô-đun phần mềm không được vi phạm các điều kiện tiên quyết của nhà cung cấp.

Thiết kế theo hợp đồng cũng có thể tạo điều kiện tái sử dụng mã, vì hợp đồng cho từng đoạn mã được ghi chép đầy đủ. Các hợp đồng cho một mô-đun có thể được coi là một dạng tài liệu phần mềm cho hành vi của mô-đun đó.

Các điều kiện hợp đồng sẽ không bao giờ bị vi phạm trong khi thực hiện chương trình không có lỗi. Các hợp đồng do đó thường chỉ được kiểm tra trong chế độ gỡ lỗi trong quá trình phát triển phần mềm. Sau khi phát hành, kiểm tra hợp đồng bị vô hiệu hóa để tối đa hóa hiệu suất.

Trong nhiều ngôn ngữ lập trình, hợp đồng thực  hiện với các assert.Asserts được mặc định biên dịch trong chế độ phát hành trong C / C ++, và tương tự như ngừng hoạt động trong C # [8] 27 và Java. Điều này có hiệu quả loại bỏ các chi phí thời gian chạy của hợp đồng phát hành.

Thiết kế theo hợp đồng không thay thế các chiến lược thử nghiệm thường xuyên, chẳng hạn như thử nghiệm đơn vị, thử nghiệm tích hợp và kiểm tra hệ thống. Thay vào đó, nó bổ sung cho thử nghiệm bên ngoài với các phép kiểm thử nội bộ có thể được kích hoạt cho cả các thử nghiệm riêng biệt và trong mã sản xuất trong giai đoạn thử nghiệm. Lợi thế của tự kiểm tra nội bộ là chúng có thể phát hiện lỗi trước khi chúng tự biểu hiện dưới dạng kết quả không hợp lệ được khách hàng quan sát. Điều này dẫn đến phát hiện lỗi sớm hơn và cụ thể hơn. 

Việc sử dụng các assert có thể được coi là một hình thức kiểm tra oracle, một cách để kiểm tra thiết kế bằng cách thực hiện hợp đồng.

 
