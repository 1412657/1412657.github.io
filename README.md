# REVEL- FRAMEWORK
## I. Giới thiệu:
### 1. Ngôn ngữ lập trình GOLANG: 
<ul> Là ngôn ngữ lập trình Server- side giới thiệu lần đầu vào năm 2009, được phát triển bởi các chuyên gia của Google. </ul>
<ul> Mục tiêu của ngôn ngữ và các công nghệ đi kèm là tạo ra một ngôn ngữ dễ thể hiện trong lập trình, hiệu quả trong biên dịch và thực thi.</ul> 
<ul> Go có nhiều nét giống với ngôn ngữ C. Go được tinh chỉnh, cải tiến hơn từ nhiều ngôn ngữ khác. Go có lợi thế trong việc xử lý đồng thời rất mới và đạt hiệu quả cao, về lập trình hướng đối tượng là rất linh hoạt.</ul>
<ul> Go là ngôn ngữ lập trình rất thích hợp cho việc xây dựng các phần mềm back-end.</ul>

###  2. Mô hình MVC:
#### a) Model: 
<ul> Cấu trúc dữ liệu theo cách tin cậy và chuẩn bị dữ liệu theo lệnh của controller 
<ul> - Là các thành phần hỗ trợ ánh xạ dữ liệu vật lý lên bộ nhớ, lưu trữ dữ liệu tạm thời trên bộ nhớ, hỗ trợ các cách thức xử lý dữ liệu, hỗ trợ khả năng giao tiếp và trao đổi dữ liệu giữa các đối tượng khác trong bộ nhớ và cơ sở dữ liệu.</ul>
<ul> - Cụ thể là một đối tượng Object trong khái niệm của lập trình hướng đối tượng OOP và mang đầy đủ khái niệm và tính chất của một Object. </ul>
</ul>

#### b) View:
<ul> Hiển thị dữ liệu cho người dùng theo cách dễ hiểu.
<ul> - Là thành phần hỗ trợ trình bày dữ liệu hay kết quả ra màn hình, hỗ trợ nhập thông tin từ phía người dùng. </ul>
<ul> - Các thành phần này có khả năng truy cập Model, truy xuất Model thông qua những hành vi mà Model cho phép nhưng View không thể thay đổi các thành phần trong Model. </ul>
</ul>

#### c) Controller:

<ul> Nhận lệnh từ người dùng, gửi lệnh đến cho model để cập nhật dữ liệu, truyền lệnh đến view để cập nhật giao diện hiển thị. 
<ul> - Là các thành phần hỗ trợ kết nối người dùng server, đón nhập yêu cầu người dùng, thực hiện chuyển xử lý, lựa chọn và cập nhật model và view tương ứng để trình bày về phía người dùng. </ul>
<ul> - Hỗ trợ kết nối giữa người model và view, giúp model xác định được view trình bày. </ul> 
</ul>

#### Quy trình xử lí web dùng mô hình MVC:
<ul>
    <li> Người dùng gọi yêu cầu xử lí tại trang chủ. </li>
    <li> Controller nhận yêu cầu và đưa lệnh sử lí yêu cầu. Các lệnh thức thi với phần View thì cập nhật hoặc phục vụ yêu cầu trang web, với Model thì để trình diễn logic. </li>
    <li> Controller truyền dữ liệu ra phần View , cập nhật giao diện hiển thị cho người dùng. Với bất kì yêu cầu nào đều phải đi qua Controller trước khi chuyển thành lệnh thực thi cho View hoặc Model. </li>
</ul>

### 3. Framework Revel:
<ul> Revel là một framework của Go, hỗ trợ Go phát triển web. </ul>
<ul> Bắt đầu một ứng dụng bằng Revel cần: 
    <ul> Cài đặt Go: 
        <ul> - Trước khi sử dụng Revel, cần cài đặt Go. </ul>
        <ul> - Thiết lập GOPATH: 
             <ul> + Gopath là nơi mà code của Go được lưu. </ul>
             <ul> + Thiết lập: 
                 <li> Tạo thư mục: mkdir ~/gocode . </li> 
                 <li> Báo cho Go biết về GOPATH: export GOPATH=~/gocode. </li>
                 <li> Lưu GOPATH để có thể áp dụng cho tất cả phiên bản: echo export GOPATH=$GOPATH >> ~/.bash_profile </li>
             </ul>
         </ul>
     </ul>
</ul>
   <ul> Cài đặt git và hg: 
        <ul> + Cài Git. </ul>
        <ul> + Cài Mercurial. </ul>
    </ul>
    <ul> Chạy framework Revel:
        <ul> + Bắt đầu revel: go get github.com/revel/revel. </ul>
        <ul> + Lấy và xây dựng tool Revel command line.</ul>
    </ul>

## II. Controller:
<ul> Revel.Controller là bối cảnh cho 1 request duy nhất.
    <li> -	Request gửi đến. </li>
    <li> -	Response phản hồi trong Hmtl, Json, Xml, File. </li>
</ul>
<ul> Controller được nhúng vào *revel.Controller như là 1 trường đầu tiên
    <ul> type MyAppController struct { 
            <ul> *revel.Controller } </ul>
    </ul>
    <ul> type MyOtherController struct {
             <ul> *revel.Controller } </ul>
             <ul> OtherStuff string </ul>
             <ul> MyNo int64 } </ul>
    </ul>          
    <ul> type FailController struct {
            <ul> XStuff string </ul>
            <ul> *revel.Controller } </ul>
    </ul>
</ul>
<ul> Revel.Controller là bối cảnh của 1 yêu cầu chứa request và dữ liệu của response. </ul>
<ul> Các thành phần được sử dụng nhiều nhất và các định nghĩa type/ struct để giúp cho Controller, Request, Params and Response. </ul>
<ul>- Controller: 
   <ul> type Controller struct { 
            <ul> Name          string  </ul>
            <ul> Type          *ControllerType </ul>
            <ul> MethodType    *MethodType  </ul> 
            <ul> AppController  interface{}  </ul>  
    </ul>
    <ul>
            <ul> Request   *Request </ul>
            <ul> Response  *Response  </ul>
            <ul> Result   Result </ul>
    </ul>
    <ul>
            <ul> Flash      Flash </ul>                 
            <ul> Session    Session  </ul>             
            <ul> Params     *Params   </ul>            
            <ul> Args       map[string]interface{} </ul>
            <ul> ViewArgs map[string]interface{} </ul>
            <ul> Validation *Validation  } </ul>          
     </ul>  
</ul>
<ul>- Request: 
   <ul> type Request struct {
            <ul> *http.Request </ul>
            <ul> ContentType string </ul>
            <ul> Format          string </ul>
            <ul> AcceptLanguages AcceptLanguages </ul>
            <ul> Locale          string </ul>
            <ul> Websocket       *websocket.Conn }</ul>
    </ul>
 </ul>
 <ul>- Params: 
    <ul> type Params struct {
            <ul> url.Values </ul>
            <ul> Files map[string][]*multipart.FileHeader } </ul>
    </ul>
</ul>
<ul>- Response: 
   <ul> type Response struct {
            <ul>  Status      int </ul>
            <ul>  ContentType string </ul>
            <ul> Headers     http.Header </ul>
            <ul> Cookies     []*http.Cookie </ul>
            <ul> Out http.ResponseWriter } </ul>
    </ul>
</ul>
    
## III. URL :
### 1. URL Router:
<ul> ULR và các Router thường được định nghĩa trong conf/ router và có 3 cột như ví dụ dưới:  
   <ul>     [METHOD]     [URL Pattern]      [Controller.Action] </ul>
   <ul>     GET             /               MySite.Welcome </ul>
</ul>

### 2. Đường dẫn cố định:
<ul> Các router sử dụng 1 sự kết hợp chính xác giữa phương thức HTTP và đường dẫn gọi ra hành động Login và About trong App Controller. 
        <ul> GET     /login                 App.Login  </ul>
        <ul> GET     /about                 App.About	</ul>
</ul>

### 3. Dấu gạch /:
<ul> GET      /hotels/               Hotels.Index </ul>
<ul> Router này chỉ đến Albums.Index cho cả /albums và /albums/ </ul> 
<ul> Định tuyến ngược của Albums.Index sẽ bao gồm cả dấu gạch chéo / </ul>
<ul> Dấu gạch chéo / không nên dùng để phân biệt giữa các hành động </ul>

### 4. Tham số URL:
<ul> GET      /hotels/:id            Hotels.Show </ul>
<ul> Mỗi phân đoạn của 1 đường dẫn có thể được kết hợp và xuất ra với một tiền tố. </ul>
<ul> Biến :id ở trên sẽ kết hợp bất kì thứ gì ngoại trừ dấu gạch chéo. </ul>
<ul> Các tham số được xuất ra và có giá trị cả trong bản đồ Controller.Params và phương pháp hành động của các tham số.  </ul>

### 5. Tham số gắn dấu *:
   <ul>  GET    /public/*filepath          Static.Serve("public") </ul>
<ul> Tham số gắn dấu * phải là phần tử đầu tiên trong đường dẫn và khớp với tất cả những phần tử còn lại trong đường dẫn. </ul>
<ul> Ví dụ: trong ví dụ trên tham  số gắn * sẽ khớp với bất kì đường dẫn nào bắt đầu với /public/, và giá trị của nó sẽ là chuỗi nằm sau dấu *. </ul>

### 6. Tham số yêu cầu và ràng buộc:
<ul> Revel đã thực hiện chuyển đổi các tham số yêu cầu sang những loại mà Go có thể dễ sử dụng và giảm rủi ro nhất có thể. </ul>
<ul> Tất cả những tham số yêu cầu được thu thập thành đối tượng Params đơn giản, bao gồm: 
    <li> - Đường dẫn URL: URL /: tham số đường dẫn cho route  </li>
    <li> - Truy vấn Vars </li>
    <li> - Mẫu Vars </li>
    <li> - Tập tin tải lên </li>
    <li> - Params hỗn hợp </li>
    <li> - Đối số hành động </li>
    <li> - Binder </li>
</ul>
## IV. Result và Response:
<ul> Hành động trả về revel.Result, giúp xử lí phản hồi HTTP và tuân theo giao diện đơn giản. 
  <ul>  type Result interface { 
     <ul>   Apply(req *Request, resp *Response) } </ul>
  </ul>
</ul>
<ul> Revel.Controller cung cấp một vài phương pháp để tạo ra nhiều kết quả khác nhau:
   <ul> - Render(), RenderTemplate(): render 1 template, truyền tham số. </ul>
   <ul> - RenderJSON(), RenderXML(): Một ứng dụng có thể gọi RenderJSON, RenderJSONP, RenderXML và truyền qua bất kì kiểu type nào của Go, thường là struct. </ul> 
   <ul> - RenderText(): trả về phản hồi dạng text </ul>
   <ul> - Redirect(): chuyển hướng đến hành động khác hoặc URL.
           <li> Hàm trợ giúp tạo ra các HTTP chuyển hướng. </li>
           <li> Sử dụng theo 2 cách và đều trả ra 1 mã trạng thái HTTP (HTTP status code) là 302 temporary redirect. </li>
   </ul>
   <ul>- Chuyển hướng đến hành động không có đối số: 
           <ul> return c.Redirect(Hotels.Settings) </ul>
   </ul>         
   <ul> - Chuyển hướng đến chuỗi đã được định dạng:
           <ul> return c.Redirect("/hotels/%d/settings", hotelId) </ul>
   </ul>
   <ul>- RenderFile(): trả về 1 tập tin, thường tải xuống dưới dạng đính kèm. </ul>
   <ul>- RenderError(): trả về phản hồi 500 để báo lỗi. </ul>
   <ul>- NotFound(): trả về phản hồi 404 để báo lỗi. </ul>
   <ul>- Todo(): trả về một phản hồi ngắn. </ul>
</ul>
<ul> Thiết lập mã trạng thái và loại nội dung: 
   <ul> - Với mỗi kết quả trả về thì đều có 1 mã trạng thái (HTTP status code) và 1 loại nội dung (content type)  </ul>
</ul>
<ul> Render: 
    <ul>- Để gọi 1 hành động, Controller.Render() đã thực hiện:
       <li> Thêm các đối số argument và ViewArg của Controller, sử dụng đinh danh cục bộ để làm khóa. </li>
       <li> Thực hiện mẫu template “view/Controller/Action.html, đi qua ViewArg của Controller như là 1 bản đồ dữ liệu.  </li>
     </ul>
     <ul>- Nếu không thành công, không tìm được template thì sẽ trả về ErrorResult thay thế. </ul>
 </ul>

## V. Template:
<ul> Revel sử dụng template trong gói htlm/templates. </ul>
<ul> Các mẫu tempalte được quét theo thứ tự:
    <ul> - Thư mục app/views trong ứng dụng và các thư mục con. </ul>
    <ul> - Thư mục templates/. </ul>
    <ul> - Nếu không thì sẽ báo lỗi 500 error (không tìm thấy template) </ul>
</ul>
<ul> Revel cung cấp mẫu cho các trang lỗi và hiển thị cho các nhà phát triển có thể thấy dễ dàng trong chế độ dev. </ul>
<ul> Render Context:
    <ul> - Revel thực thi mẫu sử dụng dữ liệu ViewArg map[string]interface{}.</ul>
    <ul> - Revel còn cung cấp :
        <li>Errors: bản đồ trả về bởi Validation.ErrorMap. </li>
        <li>Flash: dữ liệu được chỉ đến theo yêu cầu trước đó. </li>
    </ul>
</ul>
<ul> Một template có thể bao gồm nhiều template khác:
    <li>Template của GO cho phép áp dụng nhiều mẫu template khác. </li>
    <li>Ví dụ:
         <ul> {{ template “header.html” .}} </ul>
    </li>
</ul>
<ul> Template Functions (Khuôn mẫu hàm): 
    <ul> - Go cung cấp sẵn một số khung mẫu hàm <ul>
    <ul> Revel thêm vào một số hàm như:
        <li> append: thêm 1 giá trị vào mảng, tạo 1 mảng. </li>
        <li> checkbox: hỗ trợ tạo checkbox trong html. </li>
        <li> date, datetime: định dạng ngày, giờ theo mặc định của ứng dụng. </li>
        <li> even: hỗ trợ màu sắc của bảng, dòng. </li>
        <li> field: trợ giúp cho các trường đầu vào của input. 
            <ul> Cho 1 tên trường, trả về 1 struct chứa: Name, Value, Flash, Error, ErrorClass. </ul>
        </li>
        <li>   msg </li>
        <li>	nl2br: chuyển đổi dòng mới sang html.  </li>
        <li>	option: hỗ trợ tạo option trong html.  </li>
        <li>	pad </li>
        <li>	pluralize: giúp sửa đổi từ. </li>
        <li>	radio: hỗ trợ tạo các thành phần radio trong html. </li>
        <li>	raw </li>
         <li>	set: đặt biến trong ngữ cảnh cụ thể. </li>
        <li>	url: trả về reverse route cho Controller.Action </li>
        <li>	hàm tùy chỉnh: ứng dụng có thể đăng kí các hàm tùy chỉnh để sử dụng template. </li>
    </ul>
 </ul>

## Tài liệu tham khảo:
https://revel.github.io/
