Semantic Versioning 2.0.0
==============================

Tóm lược
-------

Một số phiên bản MAJOR.MINOR.PATCH, tăng dần:

1. Phiên bản MAJOR khi bạn thực hiện các thay đổi API không tương thích,
2. Phiên bản MINOR khi bạn thêm chức năng theo cách ngược lại, và
3. PATCH khi bạn sửa lỗi tương thích ngược.

Nhãn bổ sung cho siêu dữ liệu tiền phát hành và xây dựng sẵn có dưới dạng các phần mở rộng cho định dạng MAJOR.MINOR.PATCH.

Giới thiệu
------------

Trong phạm trù của quản lý phần mềm tồn tại một **dread** gọi là 
"dependency hell." Hệ thống của bạn càng lớn và càng nhiều gói tích hợp vào phần mềm của bạn,
 bạn càng có nhiều khả năng để tìm thấy chính mình, một ngày nào đó, bạn sẽ cảm thấy thất vọng.

Trong các hệ thống có nhiều phụ thuộc, phát hành phiên bản gói mới có thể nhanh chóng trở thành cơn ác mộng. Nếu thông số kỹ thuật phụ thuộc quá chặt, bạn đang gặp nguy hiểm của phiên bản khóa 
(không có khả năng để nâng cấp một gói mà không cần phải phát hành phiên bản mới của mỗi gói phụ thuộc). 
Nếu phụ thuộc được chỉ định quá lỏng lẻo,bạn chắc chắn sẽ bị cản bởi phiên hỗn tpj (giả định khả năng tương thích với các phiên bản trong tương lai hợp lý hơn)
.Dependency hell là nơi bạn đang sử dụng khi phiên bản khóa và / hoặc phiên bản quảng cáo ngăn chặn bạn
từ việc di chuyển dự án của bạn một cách dễ dàng và an toàn.

Đậy là một giải pháp cho vấn đề này,Tôi đề xuất một bộ quy tắc đơn giản và các yêu cầu mà bắt buộc làm thế nào số phiên bản được chỉ định và tăng lên.
Các quy tắc này được dựa trên nhưng không nhất thiết giới hạn ở các thực tiễn thông dụng phổ biến hiện có trước đây được sử dụng trong cả phần mềm đóng và mã nguồn mở.
Để hệ thống này hoạt động, trước hết bạn phải khai báo một API công khai.Điều này có thể bao gồm tài liệu hoặc được thực thi bởi **code itself**. 

Tôi gọi hệ thống này là "Semantic Versioning." Theo chương trình này, số phiên bản và cách họ thay đổi mang ý nghĩa về mã bên dưới và những gì đã được sửa đổi từ phiên bản này sang phiên bản kế tiếp.


Semantic Versioning Specification (SemVer)
------------------------------------------

Các từ khoá "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY",
 và "OPTIONAL" trong tài liệu này là sẽ được hiểu như mô tả trong [RFC 2119](http://tools.ietf.org/html/rfc2119).

1. Phần mềm sử dụng Semantic Versioning PHẢI khai báo một API công khai. 
API này có thể được khai báo trong chính mã hoặc tồn tại trong tài liệu. 
Tuy nhiên khi hoàn thành, nó nên chính xác và toàn diện.

2. Một phiên bản đánh số bình thường phải (MUST) theo chuẩn X.Y.Z ở đó X, Y, và Z là các số nguyên không âm, 
và phải không (MUST NOT) chứa số 0 đầu hàng. X là phiên bản chính, 
Y là phiên bản phụ và Z là phiên bản vá. Mỗi thành phần phải (MUST) tăng các con số. Cho ví dụ: 1.9.0 -> 1.10.0 -> 1.11.0.

3. Mỗi khi một phiên bản package được phát hành, các nội dung của phiên bản không được (MUST NOT) chỉnh sửa.
 Bất kỳ thay đổi nào phải (MUST) được phát hành trong phiên bản mới.

4. Phiên bản chính zero (0.y.z) dành cho sự phát triển ban đầu.
Mọi thứ có thể thay đổi bất cứ lúc nào. API công cộng không được coi là ổn định.

5. Phiên bản 1.0.0 định nghĩa API công khai. Cách thức mà số phiên bản được tăng 
lên sau khi bản phát hành này phụ thuộc vào API công khai này và cách nó thay đổi.

6. Phiên bản vá Z (x.y.Z | x > 0) phải (MUST) được tăng nếu chỉ sửa các lỗi phát sinh mà vẫn tương thích với phiên bản cũ.
 Việc sửa lỗi được định nghĩa là các thay đổi bên trong để khắc phục các hành vi không chính xác.

7. Phiên bản phụ Y (x.Y.z | x > 0) phải (MUST) được tăng nếu tính năng mới tương thích với API public đã được giới thiệu. 
Nó phải (MUST) được tăng nếu bất kỳ tính năng API public được đánh dấu là không dùng nữa. 
Nó có thể (MAY) được tăng nếu tính năng mới là đáng kể hoặc cải tiến trong private code. 
Nó có thể (MAY) bao hồm các mức thay đổi của bản vá. Phiên bản vá phải MUST được đưa về khi phiên bản phụ tăng.

8. Phiên bản chính X (X.y.z | X > 0) phải (MUST) được tăng nếu mọi thay đổi không tương thích với API public đã giới thiệu. 
Nó có thể (MAY) cũng bao gồm các mức thay đổi bản phụ và bản vá.Bản vá và bản phụ phải được đưa về 0 khi phiên bản chính tăng.

9. Một phiên bản pre-release có thể (MAY) được biểu thị bằng cách thêm dấu gạch ngang '-' và một chuỗi dấu chấm '.' để định danh ngay sau phiên bản vá lỗi (patch version). Các tên định danh phải (MUST) chỉ bao bồm các ký tự ASCII và dấu gạch ngang [0-9A-Za-z-]. Các tên định danh không được (MUST NOT) trống. Số trong định danh phải không (MUST NOT) bao gồm số 0 ở đầu. 
Phiên bản pre-release có quyền ưu tiên thấp hơn phiên bản bình thường. 
Một phiên bản pre-release là phiên bản không ổn định và có thể không đáp ứng về tính tương thích như các phiên bản bình thường.
Ví dụ: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.

10. Các bản metadata có thể (MAY) được biểu thị bằng cách thêm các một dấu cộng '+' và một loạt các dấu chấm '.' để tách các định danh ngay sau số hiệu của các bản vá hoặc bản pre-release. Các định danh phải (MUST) chỉ bao gồm các ký tự ASCII và dấu gạch ngang [0-9A-Za-z-].Các định danh không được (MUST NOT) trống. Các bản metadata phải (MUST) được bỏ qua khi xác định độ ưu tiên của các phiên bản. 
Do đó hai phiên bản mà chỉ khác nhau ở bản metadat thì có thể được coi là tương đồng. Ví dụ: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.

11. Làm thế nào so sánh thứ tự ưu tiên giữa các phiên bản.
 Quyền ưu tiên phải (MUST) được tính toán bằng cách tách các phiên bản thành số nhận diện phiên bản chính (major), phụ (minor), bản vá (patch) và tiền phát hành (pre-release) trong khi gọi (Bản metadata không được tính vào quyền ưu tiên). Precedence được xác định bởi sự khác biệt đầu tiên khi so sánh mỗi định danh từ trái sang phải: phiên bản Major, minor, và patch luôn luôn được so sánh về số. Ví dụ: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1.Khi các phiên bản major, minor, và patch bằng nhau, một phiên bản pre-release có ưu tiên thấp hơn phiên bản bình thường. Ví dụ: 1.0.0-alpha < 1.0.0. Quyền ưu tiên cho 2 phiên bản pre-release mà giống nhau về phiên bản major, minor, và patch phải (MUST) được xác định bằng cách so sánh mỗi dấu phân tách từ trái sang phải cho đến khi tìm thấy một sự khác biệt: 
 định danh chỉ bao gồm các chữ số được so sánh về số và định danh với chữ cái hoặc dấu gạch ngang được so sánh theo thứ thự ASCII. 
 Các định danh số luôn có độ ưu tiên thấp hơn các định danh không phải là số. 
 Một tập lớn các bản pre-release có ưu tiên lớn hơn so với bản nhỏ hơn, nếu tất cả các định danh trước đố bằng nhau Ví dụ: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.

Backus–Naur Form Grammar for Valid SemVer Versions
--------------------------------------------------

    <valid semver> ::= <version core>
                     | <version core> "-" <pre-release>
                     | <version core> "+" <build>
                     | <version core> "-" <pre-release> "+" <build>

    <version core> ::= <major> "." <minor> "." <patch>

    <major> ::= <numeric identifier>

    <minor> ::= <numeric identifier>

    <patch> ::= <numeric identifier>

    <pre-release> ::= <dot-separated pre-release identifiers>

    <dot-separated pre-release identifiers> ::= <pre-release identifier>
                                              | <pre-release identifier> "." <dot-separated pre-release identifiers>

    <build> ::= <dot-separated build identifiers>

    <dot-separated build identifiers> ::= <build identifier>
                                        | <build identifier> "." <dot-separated build identifiers>

    <pre-release identifier> ::= <alphanumeric identifier>
                               | <numeric identifier>

    <build identifier> ::= <alphanumeric identifier>
                         | <digits>

    <alphanumeric identifier> ::= <non-digit>
                                | <non-digit> <identifier characters>
                                | <identifier characters> <non-digit>
                                | <identifier characters> <non-digit> <identifier characters>

    <numeric identifier> ::= "0"
                           | <positive digit>
                           | <positive digit> <digits>

    <identifier characters> ::= <identifier character>
                              | <identifier character> <identifier characters>

    <identifier character> ::= <digit>
                             | <non-digit>

    <non-digit> ::= <letter>
                  | "-"

    <digits> ::= <digit>
               | <digit> <digits>

    <digit> ::= "0"
              | <positive digit>

    <positive digit> ::= "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

    <letter> ::= "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J"
               | "K" | "L" | "M" | "N" | "O" | "P" | "Q" | "R" | "S" | "T"
               | "U" | "V" | "W" | "X" | "Y" | "Z" | "a" | "b" | "c" | "d"
               | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n"
               | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x"
               | "y" | "z"


Tại sao dùng Semantic Versioning?
----------------------------

Đây không phải là một ý tưởng mới hay cách mạng. Trên thực tế, bạn có thể đã làm một cái gì đó gần giống với điều này.
 Vấn đề là "close" đó không đủ tốt. Nếu không tuân thủ một số loại đặc tả chính thức, số phiên bản chủ yếu không có ích cho quản lý phụ thuộc. 
 Bằng cách đặt tên và định nghĩa rõ ràng cho những ý tưởng trên, sẽ dễ dàng truyền đạt ý định của bạn cho người dùng phần mềm của bạn.
  Một khi các ý định này là rõ ràng, cuối cùng có thể được tạo ra đặc điểm phụ thuộc (nhưng không quá linh hoạt).

Một ví dụ đơn giản sẽ chứng minh làm thế nào Semantic Versioning có thể làm cho **dependency
hell** là một điều của quá khứ. Xem xét một thư viện được gọi là "Firetruck." Nó đòi hỏi 
Semantically Versioned gói có tên "Ladder." Vào thời điểm Firetruck được tạo ra,
 Ladder ở phiên bản 3.1.0. Kể từ Firetruck sử dụng một số chức năng đã được giới thiệu lần đầu tiên trong 3.1.0,
  bạn có thể chỉ định một cách an toàn sự phụ thuộc Ladder lớn hơn hoặc bằng 3.1.0 nhưng ít hơn 4.0.0. Bây giờ,
   khi Ladder phiên bản 3.1.1 và 3.2.0 trở nên có sẵn,
   bạn có thể phát hành chúng vào hệ thống quản lý gói và biết rằng chúng sẽ tương thích với phần mềm phụ thuộc hiện có.

Là một nhà phát triển có trách nhiệm, bạn sẽ, tất nhiên, muốn xác minh rằng bất kỳ chức năng nâng cấp gói nào đều được công bố. Thực tế đó là một nơi lộn xộn,
không có gì chúng ta có thể làm được về điều đó nhưng phải thận trọng. Bạn có thể làm gì
Semantic Versioning cung cấp cho bạn một cách phát hành và nâng cấp gói mà không cần phải gọi lại các phụ thuộc của phiên bản mới, tiết kiệm thời gian và tránh rắc rối.

Nếu tất cả những điều này là mong muốn, tất cả những gì bạn cần làm để bắt đầu sử dụng Semantic
Versioning để khai báo những gì bạn làm và tuân thủ quy tắc đó. Liên kết tới trang web này từ README của bạn để những người khác biết các quy tắc và có thể có ích từ chúng.


FAQ
---

### Làm thế nào tôi nên đối phó với các phiên bản trong giai đoạn phát triển ban đầu 0.y.z?

Điều đơn giản nhất để làm là bắt đầu phát hành phát triển ban đầu của bạn tại 0.1.0
và sau đó tăng các phiên bản nhỏ cho mỗi bản phát hành tiếp theo.

### How do I know when to release 1.0.0?

If your software is being used in production, it should probably already be
1.0.0. If you have a stable API on which users have come to depend, you should
be 1.0.0. If you're worrying a lot about backwards compatibility, you should
probably already be 1.0.0.

### Doesn't this discourage rapid development and fast iteration?

Major version zero is all about rapid development. If you're changing the API
every day you should either still be in version 0.y.z or on a separate
development branch working on the next major version.

### If even the tiniest backwards incompatible changes to the public API require a major version bump, won't I end up at version 42.0.0 very rapidly?

This is a question of responsible development and foresight. Incompatible
changes should not be introduced lightly to software that has a lot of
dependent code. The cost that must be incurred to upgrade can be significant.
Having to bump major versions to release incompatible changes means you'll
think through the impact of your changes, and evaluate the cost/benefit ratio
involved.

### Documenting the entire public API is too much work!

It is your responsibility as a professional developer to properly document
software that is intended for use by others. Managing software complexity is a
hugely important part of keeping a project efficient, and that's hard to do if
nobody knows how to use your software, or what methods are safe to call. In
the long run, Semantic Versioning, and the insistence on a well defined public
API can keep everyone and everything running smoothly.

### What do I do if I accidentally release a backwards incompatible change as a minor version?

As soon as you realize that you've broken the Semantic Versioning spec, fix
the problem and release a new minor version that corrects the problem and
restores backwards compatibility. Even under this circumstance, it is
unacceptable to modify versioned releases. If it's appropriate,
document the offending version and inform your users of the problem so that
they are aware of the offending version.

### What should I do if I update my own dependencies without changing the public API?

That would be considered compatible since it does not affect the public API.
Software that explicitly depends on the same dependencies as your package
should have their own dependency specifications and the author will notice any
conflicts. Determining whether the change is a patch level or minor level
modification depends on whether you updated your dependencies in order to fix
a bug or introduce new functionality. I would usually expect additional code
for the latter instance, in which case it's obviously a minor level increment.

### What if I inadvertently alter the public API in a way that is not compliant with the version number change (i.e. the code incorrectly introduces a major breaking change in a patch release)?

Use your best judgment. If you have a huge audience that will be drastically
impacted by changing the behavior back to what the public API intended, then
it may be best to perform a major version release, even though the fix could
strictly be considered a patch release. Remember, Semantic Versioning is all
about conveying meaning by how the version number changes. If these changes
are important to your users, use the version number to inform them.

### How should I handle deprecating functionality?

Deprecating existing functionality is a normal part of software development and
is often required to make forward progress. When you deprecate part of your
public API, you should do two things: (1) update your documentation to let
users know about the change, (2) issue a new minor release with the deprecation
in place. Before you completely remove the functionality in a new major release
there should be at least one minor release that contains the deprecation so
that users can smoothly transition to the new API.

### Does SemVer have a size limit on the version string?

No, but use good judgment. A 255 character version string is probably overkill,
for example. Also, specific systems may impose their own limits on the size of
the string.

### Is "v1.2.3" a semantic version?

No, "v1.2.3" is not a semantic version. However, prefixing a semantic version
with a "v" is a common way (in English) to indicate it is a version number.
Abbreviating "version" as "v" is often seen with version control. Example:
`git tag v1.2.3 -m "Release version 1.2.3"`, in which case "v1.2.3" is a tag
name and the semantic version is "1.2.3".


About
-----

The Semantic Versioning specification is authored by [Tom
Preston-Werner](http://tom.preston-werner.com), inventor of Gravatar and
cofounder of GitHub.

If you'd like to leave feedback, please [open an issue on
GitHub](https://github.com/mojombo/semver/issues).


License
-------

Creative Commons - CC BY 3.0
http://creativecommons.org/licenses/by/3.0/
