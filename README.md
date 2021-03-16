## Thực hành Khai phá Dữ liệu

# Khai phá dữ liệu Spanish Rail Tickets Pricing - Renfe

## Giới thiệu
Spanish Rail Tickets Pricing - Renfe là bộ dữ liệu về các chuyến đi của Hệ thống tàu cao tốc Tây Ban Nha của công ty Renfe. Bộ dữ liệu này gồm các thông tin di chuyển của hành khách từ ngày 11/04/2019 đến ngày 7/10/2020. Các thông tin của mỗi chuyến đi bao gồm nơi khởi hành, nơi đến, hạng vé, chỗ ngồi, số ghế trống... Chúng ta hãy cùng phân tích một cách trực quan bộ dữ liệu này bằng EDA(Exploratory data analysis) để tìm hiểu hành vi tiêu dùng của họ. 

Dataset: [Spanish Rail Tickets Pricing - Renfe](https://www.kaggle.com/thegurusteam/spanish-high-speed-rail-system-ticket-pricing)

**Notebooks**:
+ [Phân tích dữ liệu Tàu cao tốc Renfe ở Tây Ban Nha](https://github.com/hoangtv2000/data-mining/blob/main/Ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u%20T%C3%A0u%20cao%20t%E1%BB%91c%20Renfe%20%E1%BB%9F%20T%C3%A2y%20Ban%20Nha.ipynb)
+ [Xây dựng mô hình dự đoán giá vé tàu cao tốc Renfe ở Tây Ban Nha](https://github.com/hoangtv2000/data-mining/blob/main/X%C3%A2y%20d%E1%BB%B1ng%20m%C3%B4%20h%C3%ACnh%20d%E1%BB%B1%20%C4%91o%C3%A1n%20gi%C3%A1%20v%C3%A9%20t%C3%A0u%20cao%20t%E1%BB%91c%20Renfe%20%E1%BB%9F%20T%C3%A2y%20Ban%20Nha.ipynb)

## Mục lục
  * [Các phân tích & minh họa](#các-phân-tích--minh-họa)
    + [1. Thống kê những ngày có nhiều lượt khởi hành nhất](#1-thống-kê-những-ngày-có-nhiều-lượt-khởi-hành-nhất)
    + [2. Thống kê các chuyến tàu khởi hành và kết thúc cùng ngày và khác ngày](#2-thống-kê-các-chuyến-tàu-khởi-hành-và-kết-thúc-cùng-ngày-và-khác-ngày)
    + [3. Thống kê giờ khởi hành của các chuyến tàu](#3-thống-kê-giờ-khởi-hành-của-các-chuyến-tàu)
    + [4. Thống kê giờ kết thúc của các chuyến tàu](#4-thống-kê-giờ-kết-thúc-của-các-chuyến-tàu)
    + [5. Thống kê số chuyến tàu của các tháng](#5-thống-kê-số-chuyến-tàu-của-các-tháng)
    + [6. Thống kê thời gian di chuyển của các chuyến tàu](#6-thống-kê-thời-gian-di-chuyển-của-các-chuyến-tàu)
    + [7. Thống kê lượt tàu chạy của các ngày trong tuần](#7-thống-kê-lượt-tàu-chạy-của-các-ngày-trong-tuần)
    + [8. Lộ trình](#8-lộ-trình)
    + [9. Phân tích các loại tàu cao tốc](#9-phân-tích-các-loại-tàu-cao-tốc)
    + [10. Phân tích các hạng vé](#10-phân-tích-các-hạng-vé)
    + [11. Phân tích loại vé](#11-phân-tích-loại-vé)
    + [12. Phân tích Lộ trình với các yếu tố khác](#12-phân-tích-lộ-trình-với-các-yếu-tố-khác)
      - [Phân tích Lộ trình với Loại tàu cao tốc](#phân-tích-lộ-trình-với-loại-tàu-cao-tốc)
      - [Phân tích Lộ trình với Hạng vé](#phân-tích-lộ-trình-với-hạng-vé)
    + [13. Phân tích giá vé trung bình dựa trên Hạng vé, Loại tàu cao tốc, Lộ trình và Loại vé](#13-phân-tích-giá-vé-trung-bình-dựa-trên-hạng-vé-loại-tàu-cao-tốc-lộ-trình-và-loại-vé)
      - [Biểu đồ trung bình giá vé theo Hạng vé](#biểu-đồ-trung-bình-giá-vé-theo-hạng-vé)
      - [Biểu đồ trung bình giá vé theo Loại tàu cao tốc](#biểu-đồ-trung-bình-giá-vé-theo-loại-tàu-cao-tốc)
      - [Biểu đồ trung bình giá vé theo Lộ trình](#biểu-đồ-trung-bình-giá-vé-theo-lộ-trình)
      - [Biểu đồ trung bình giá vé theo Loại vé](#biểu-đồ-trung-bình-giá-vé-theo-loại-vé)
    + [14. Phân tích thời gian di chuyển trung bình dựa theo Lộ trình](#14-phân-tích-thời-gian-di-chuyển-trung-bình-dựa-theo-lộ-trình)
    + [15. Phân tích thời gian di chuyển trung bình dựa theo Loại tàu cao tốc](#15-phân-tích-thời-gian-di-chuyển-trung-bình-dựa-theo-loại-tàu-cao-tốc)
  * [Xử lý dữ liệu và xây dựng mô hình dự đoán giá vé](#xử-lý-dữ-liệu-và-xây-dựng-mô-hình-dự-đoán-giá-vé)
    + [1. Xử lý dữ liệu ](#1-xử-lý-dữ-liệu) 
    + [2. Xây dựng mô hình SVRregression](#2-xây-dựng-mô-hình-svrregression) 
    + [3. Xây dựng mô hình Gradient boosting by Random forest (GBRF)](#3-xây-dựng-mô-hình-gradient-boosting-by-random-forest-gbrf)
    + [Kết luận](#kết-luận)



## Các phân tích & minh họa 
**Lưu ý**: để thuận tiện cho việc xem biểu đồ, hãy để github ở chế độ light mode.

### 1. Thống kê những ngày có nhiều lượt khởi hành nhất 
Các ngày từ ngày 13 đến 17 tháng 4 có lượt khởi hành nhiều nhất, do những ngày này là ngày lễ thứ 5 thánh và thứ 6 tuần thánh của người Tây Ban Nha.

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/50%20ng%C3%A0y%20c%C3%B3%20nhi%E1%BB%81u%20l%C6%B0%E1%BB%A3t%20kh%E1%BB%9Fi%20h%C3%A0nh%20nh%E1%BA%A5t.png'>

### 2. Thống kê các chuyến tàu khởi hành và kết thúc cùng ngày và khác ngày
Hầu hết các chuyến tàu bắt đầu và kết thúc trong ngày, chỉ có hơn 1% chuyến tàu là khác ngày.

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/%25%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20kh%E1%BB%9Fi%20h%C3%A0nh%20v%C3%A0%20k%E1%BA%BFt%20th%C3%BAc%20c%C3%B9ng%20ng%C3%A0y.png'>

### 3. Thống kê giờ khởi hành của các chuyến tàu
Hầu hết các chuyến tàu khởi hành từ 6AM đến 9AM hoặc từ 2PM đến 7PM. Tầm giờ đó là giờ cao điểm.

**Biểu đồ cột**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Gi%E1%BB%9D%20kh%E1%BB%9Fi%20h%C3%A0nh%20c%E1%BB%A7a%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u.png'>


**Biểu đồ sao**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/S%E1%BB%91%20l%C6%B0%E1%BB%A3ng%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20kh%E1%BB%9Fi%20h%C3%A0nh%20theo%20gi%E1%BB%9D.png'>


### 4. Thống kê giờ kết thúc của các chuyến tàu
Hầu hết các chuyến tàu kết thúc từ 9AM đến 11AM hoặc từ 17PM đến 22PM.

**Biểu đồ cột**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20gi%E1%BB%9D%20k%E1%BA%BFt%20th%C3%BAc%20c%E1%BB%A7a%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u.png'>


**Biểu đồ sao**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/S%E1%BB%91%20l%C6%B0%E1%BB%A3ng%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20k%E1%BA%BFt%20th%C3%BAc%20theo%20gi%E1%BB%9D.png'>


### 5. Thống kê số chuyến tàu của các tháng
Hầu hết các chuyến tàu nằm ở tháng 3

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20s%E1%BB%91%20chuy%E1%BA%BFn%20t%C3%A0u%20c%E1%BB%A7a%20c%C3%A1c%20th%C3%A1ng.png'>


### 6. Thống kê thời gian di chuyển của các chuyến tàu
Đa số các chuyến tàu có thời gian di chuyển ở khoảng 150 - 170 phút, đây là thời gian trung bình để đi từ Madrid tới Barcelona hoặc từ Madrid tới Seville.

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20th%E1%BB%9Di%20gian%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20(d%E1%BB%B1a%20tr%C3%AAn%2040k%20quan%20s%C3%A1t).png'>


### 7. Thống kê lượt tàu chạy của các ngày trong tuần
Ngày thứ 6 và thứ 7 cuối tuần có lượt tàu chạy nhiều hơn những ngày còn lại. 

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20l%C6%B0%E1%BB%A3t%20t%C3%A0u%20c%E1%BB%A7a%20c%C3%A1c%20ng%C3%A0y%20trong%20tu%E1%BA%A7n.png'>


### 8. Lộ trình
Trong dataset có tất cả 62 lộ trình. Hầu hết các lộ trình đều xuất phát từ Madrid và chọn Madrid làm điểm đến. Tiếp đến là hai thành phố Barcelona, Vanlencia và Seville. 

**Biểu đồ tròn thống kê top 20 lộ trình được lựa chọn nhiều nhất theo tỉ lệ phần trăm**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Bi%E1%BB%83u%20%C4%91%E1%BB%93%20top%2020%20l%E1%BB%99%20tr%C3%ACnh%20%C4%91%C6%B0%E1%BB%A3c%20ch%E1%BB%8Dn%20nhi%E1%BB%81u%20nh%E1%BA%A5t.png'>


**Đồ thị cây thống kê top 20 lộ trình được lựa chọn nhiều nhất**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Ph%C3%A2n%20t%C3%ADch%20l%E1%BB%99%20tr%C3%ACnh%20b%E1%BA%B1ng%20%C4%91%E1%BB%93%20th%E1%BB%8B%20c%C3%A2y.png'>


### 9. Phân tích các loại tàu cao tốc

+ **Tàu AVE**: Tàu AVE hoạt động trên hệ thống đường ray 3100 km, là đường ray tốc độ cao dài nhất ở Châu Âu. Tàu AVE có thể chạy với tốc độ lên đến 310 km/h trên mạng lưới đường ray rộng lớn này, cho phép di chuyển một cách nhanh chóng giữa các thành phố ở Tây Ban Nha. Nó có thể đi từ Madrid đến Barcelona trong vòng chưa đầy 3 giờ! Hệ thống xe lửa hiện đại này kết nối nhiều thành phố trên khắp Tây Ban Nha từ Madrid và Barcelona, đến Córdoba, Seville, Málaga và Valencia.
+ **ALVIA**: Các chuyến tàu Alvia của Tây Ban Nha kết hợp cả tuyến đường dài và dịch vụ tốc độ cao để kết nối các thành phố lớn trên khắp Tây Ban Nha. Alvia cung cấp nhiều tuyến đường như kết nối từ Madrid đến Gijón, Alicante và Castellón và từ Barcelona đến Bilbao, A Coruña và Vigo. Với các toa máy lạnh và check-in control trước khi lên tàu, Alvia là một sự lựa chọn thoải mái và thư giãn để đi qua một trong những quốc gia lớn nhất châu Âu.
+ **NỘI TỈNH**: Các chuyến tàu nội địa tỉnh và liên tỉnh ở Tây Ban Nha. Các chuyến tàu nội tỉnh hoạt động ở phía bắc của Tây Ban Nha, kết nối các thành phố như Bilbao, Gijón, León và Santander. Đây là một mạng lưới các chuyến tàu hoạt động trong và xung quanh các thành phố lớn của Tây Ban Nha bao gồm Barcelona và Valencia.
+ **LIÊN TỈNH**: Các chuyến tàu liên tỉnh truyền thống chạy với tốc độ từ 160 đến 250 km / h cho phép bạn đến gần như mọi ngóc ngách của Tây Ban Nha. Bạn có thể chọn đi hạng 2 (du lịch) hoặc hạng 1 (ưu tiên). Độ thoải mái của toa gần bằng với tàu cao tốc AVE. Tất cả các chuyến tàu đều có máy lạnh.
+ **AV City**: Các chuyến tàu của thành phố AV là tàu cao tốc bổ sung cho AVE, cung cấp giá thấp hơn và được bán trên thị trường ở hạng phổ thông và hạng phổ thông plus (p +).
+ **TRENHOTEL**: Trenhotel là các chuyến tàu đêm chạy ở Tây Ban Nha và từ Tây Ban Nha đến Bồ Đào Nha. Có nhiều loại tàu khác nhau được sử dụng, cung cấp các loại dịch vụ khác nhau. Các chuyến tàu cũ có ghế hạng 2, 4 giường, 2 giường và 2 giường với vòi sen tắm riêng và nhà vệ sinh. Các chuyến tàu mới hơn có ghế ngả hạng 1 và 2 giường nằm với vòi sen và nhà vệ sinh riêng. Tất cả các chuyến tàu đều có toa hàng nhỏ.
+ **LD,AVE-MD,AVE-LD,LD-MD,MD-AVE,MD,LD-AVE** là các chuyến tàu LD-MD là Long Distance/ Medium Distance

**Phân tích các loại tàu cao tốc bằng biểu đồ tròn**

Đa số người dân sử dụng loại tàu AVE. Đây là loại tàu hoạt động trên hệ thống đường ray nối các thành phố lớn (Madrid, Barcelona, Vallencia,...) 

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Ph%C3%A2n%20t%C3%ADch%20c%C3%A1c%20lo%E1%BA%A1i%20t%C3%A0u%20cao%20t%E1%BB%91c%20b%E1%BA%B1ng%20bi%E1%BB%83u%20%C4%91%E1%BB%93%20tr%C3%B2n.png'>


### 10. Phân tích các hạng vé

Các chuyến tàu ở Tây Ban Nha thường được chia làm 2 hạng vé:
+ **Turista**: bình dân
+ **Preferente**: hạng sang

**Phân tích các hạng vé bằng biểu đồ tròn**

Hơn 80% hành khách chọn vé hạng bình dân, và chỉ 5% chọn vé hạng sang.

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Ph%C3%A2n%20t%C3%ADch%20c%C3%A1c%20h%E1%BA%A1ng%20v%C3%A9%20b%E1%BA%B1ng%20bi%E1%BB%83u%20%C4%91%E1%BB%93%20tr%C3%B2n.png'>


### 11. Phân tích loại vé

+ **Promo**: Các chương trình khuyến mại này dựa trên hệ thống giá vé động với chiết khấu lớn với các chuyến tàu AVE và Larga Distancia (Đường dài) trên các hành trình nội địa, được thiết lập tùy thuộc vào chuyến tàu, ngày đi và lượt mua trước.
+ **Flexible**: là chương trình ưu đãi thương mại chỉ dành cho các dịch vụ AVE và Larga Distancia (Đường dài) trên tất cả các hạng ghế và chỗ ngồi (chỗ ngồi và bến). Đây là mức giá tương tự như bình thường, không có bất kỳ chiết khấu nào, nhưng đi kèm với các ưu đãi bổ sung giúp hành khách có điều kiện tốt hơn để thay đổi, hủy chuyến hoặc nếu họ lỡ chuyến tàu của mình.
+ **Promo +**: Các chương trình khuyến mại này dựa trên hệ thống giá vé động với chiết khấu lớn với các chuyến tàu AVE và Larga Distancia (Đường dài) trên các hành trình nội địa, được thiết lập tùy thuộc vào chuyến tàu, ngày đi và lượt mua trước. Nhưng không hạ thấp bất kỳ tiêu chuẩn chất lượng nào.

**Phân tích các loại vé bằng biểu đồ tròn**

Hơn 50% hành khách chọn vé loại Promo, 22% chọn Flexible.

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Ph%C3%A2n%20t%C3%ADch%20c%C3%A1c%20lo%E1%BA%A1i%20v%C3%A9%20b%E1%BA%B1ng%20bi%E1%BB%83u%20%C4%91%E1%BB%93%20tr%C3%B2n.png'>


### 12. Phân tích Lộ trình với các yếu tố khác

#### Phân tích Lộ trình với Loại tàu cao tốc
Biểu đồ thống kê các chuyến đi với Loại tàu cao tốc dựa trên Lộ trình:

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Bi%E1%BB%83u%20%C4%91%E1%BB%93%20th%E1%BB%91ng%20k%C3%AA%20c%C3%A1c%20chuy%E1%BA%BFn%20%C4%91i%20v%E1%BB%9Bi%20Lo%E1%BA%A1i%20t%C3%A0u%20cao%20t%E1%BB%91c%20d%E1%BB%B1a%20tr%C3%AAn%20L%E1%BB%99%20tr%C3%ACnh.png'>

#### Phân tích Lộ trình với Hạng vé
Biểu đồ thống kê các chuyến đi với Hạng vé dựa trên Lộ trình

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Bi%E1%BB%83u%20%C4%91%E1%BB%93%20th%E1%BB%91ng%20k%C3%AA%20c%C3%A1c%20chuy%E1%BA%BFn%20%C4%91i%20v%E1%BB%9Bi%20H%E1%BA%A1ng%20v%C3%A9%20d%E1%BB%B1a%20tr%C3%AAn%20L%E1%BB%99%20tr%C3%ACnh.png'>


### 13. Phân tích giá vé trung bình dựa trên Hạng vé, Loại tàu cao tốc, Lộ trình và Loại vé

#### Biểu đồ trung bình giá vé theo Hạng vé
<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/scatter0.png'>

#### Biểu đồ trung bình giá vé theo Loại tàu cao tốc
<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/scatter1.png'>

#### Biểu đồ trung bình giá vé theo Lộ trình
<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/scatter2.png'>

#### Biểu đồ trung bình giá vé theo Loại vé
<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/scatter3.png'>

### 14. Phân tích thời gian di chuyển trung bình dựa theo Lộ trình
Biểu đồ thời gian di chuyển trung bình dựa theo Lộ trình

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/scatter4.png'>

### 15. Phân tích thời gian di chuyển trung bình dựa theo Loại tàu cao tốc
Biểu đồ thời gian di chuyển trung bình dựa theo Loại tàu cao tốc

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/scatter5.png'>


## Xử lý dữ liệu và xây dựng mô hình dự đoán giá vé 

### 1. Xử lý dữ liệu 

Dữ liệu đầu vào có shape là: (38753060, 14)

Công đoạn xử lý dữ liệu bao gồm: 

+ Điền giá trị thiếu
+ Tách thông tin thời gian nhập dữ liệu, thời gian khởi hành và thời gian đến thành các giá trị riêng
+ Quan sát dữ liệu bằng ma trận tương quan, lược bỏ một số cột có correlation cao
+ Quan sát và các cột chỉ có 1 loại feature hoặc các cột có feature là metadata
+ One-hot encoding các cột là categorical features, dữ liệu sau xử lý có shape là (38753060, 721)

**Cấu hình PC thực nghiệm**: CPU Intel core i5-8300H 2.3 GHz Processor, 16GB RAM, GPU Nvidia GeForge GTX 1050.

### 2. Xây dựng mô hình SVRregression
**Giới thiệu về SVR** 

SVR là thuật toán hồi quy dựa trên ý tưởng của thuật toán phân loại SVM. Thay vì tối ưu hàm mất mát thỏa mãn với tất cả các điểm trong tập dữ liệu như các thuật toán Linear Regression. SVR cung cấp sai số dự đoán &alpha; và đảm bảo rằng hầu hết các điểm trong tập dữ liệu đều nằm trong miền **Wx+b-&alpha;** &leq; **Wx+b** &leq; **Wx+b+&alpha;** (với  Wx+b = y&#770; là giá trị dự đoán).

**Training**

Dữ liệu được chia train test theo tỉ lệ 100/1. Sử dụng mô hình SVR của framework sklearn. Thời gian train là **15 phút**. 

**Kết quả**

Kết quả thu được trên tập test với độ chính xác **70.3%**.


### 3. Xây dựng mô hình Gradient boosting by Random forest (GBRF)
**Giới thiệu về GBRF** 

GBRF là thuật toán học có giám sát dựa trên việc xây dựng và kết hợp các weak learners thành một strong learner, trong trường hợp này, chúng là các Decision tree. Cho ***N*** decision tree được xây dựng bởi một tập subset-feature ngẫu nhiên. Các leaf của tree là các giá trị dự đoán. Thuật toán sẽ tối ưu bằng cách đưa dữ liệu vào các tree một cách tuần tự và tính residual (residual có thể được tính bằng MSE hoặc logarithmic loss giữa giá trị dự đoán và giá trị thực). 

Ta gọi kết quả dự đoán khi dữ liệu đi qua tree thứ *k* = **trung bình giá trị thực** + **learning_rate**x(&sum;<sub>i=1</sub><sup>k</sup> residual của tree thứ *i*). 

Từ kết quả này, tree thứ *k+1* sẽ học cách tối ưu dựa trên các tree từ *k* trở về trước.

Kết quả tối ưu cuối cùng là kết quả đi qua ***N*** tree.

**Tiến trình học của Random forest**  

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/1%20swdff6XNZiwzKdtu3pfN9A.png' alt="Tiến trình học của Random forest" width="800" height="300">

**Tiến trình học của GBRF**  

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/1%20X1sm0JVpRS2n3Hs2TTmRFQ.png' alt="Tiến trình học của Gradient boosting by Random forest" width="800" height="300">

**Training**

Dữ liệu được chia train test theo tỉ lệ 100/1. Sử dụng mô hình LGBMRegressor của framework lightgbm. Thời gian train là **15 phút**. Với ***N*** = 1000, **learning_rate** = 0.1.

**Kết quả**

Kết quả thu được trên tập test với độ chính xác **90%**.

### Kết luận
Thuật toán GBRF cho kết quả tốt hơn và thời gian training nhanh hơn SVRegression khá nhiều. Tuy nhiên, để thuật toán GBRF hoạt động hiệu quả, ta cần phải tunning 2 hyperparameter: ***N*** (số lượng tree khởi tạo) và **learning_rate** (tốc độ học). Nếu ***N*** quá lớn, thời gian training và implementing sẽ rất lâu và có thể gây ra hiện tượng overfitting.

