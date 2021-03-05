# Thực hành Khai phá Dữ liệu với một số Dataset
**Lưu ý**: để thuận tiện cho việc xem biểu đồ, hãy để github ở chế độ light mode.

# Dữ liệu về giá vé tàu cao tốc ở Tây Ban Nha

## Giới thiệu
Đây là bộ dữ liệu về các chuyến đi của Hệ thống tàu cao tốc Tây Ban Nha của công ty Renfe. Trong bộ dữ liệu này gồm các thông tin di chuyển của hành khách từ ngày 11/04/2019 đến ngày 7/10/2020. Các thông tin của mỗi chuyến đi gồm nơi khởi hành, nơi đến, hạng vé, chỗ ngồi, số ghế trống... Chúng ta hãy cùng phân tích một cách trực quan bộ dữ liệu này bằng EDA(Exploratory data analysis) để tìm hiểu hành vi tiêu dùng của họ. 

Dataset: [Spanish Rail Tickets Pricing - Renfe](https://www.kaggle.com/thegurusteam/spanish-high-speed-rail-system-ticket-pricing)

## Các phân tích & minh họa 

### 1. Thống kê những ngày có nhiều lượt khởi hành nhất 

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/50%20ng%C3%A0y%20c%C3%B3%20nhi%E1%BB%81u%20l%C6%B0%E1%BB%A3t%20kh%E1%BB%9Fi%20h%C3%A0nh%20nh%E1%BA%A5t.png'>

### 2. Thống kê các chuyến tàu khởi hành và kết thúc cùng ngày và khác ngày

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/%25%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20kh%E1%BB%9Fi%20h%C3%A0nh%20v%C3%A0%20k%E1%BA%BFt%20th%C3%BAc%20c%C3%B9ng%20ng%C3%A0y.png'>

### 3. Thống kê giờ khởi hành của các chuyến tàu

**Biểu đồ cột**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Gi%E1%BB%9D%20kh%E1%BB%9Fi%20h%C3%A0nh%20c%E1%BB%A7a%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u.png'>


**Biểu đồ sao**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/S%E1%BB%91%20l%C6%B0%E1%BB%A3ng%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20kh%E1%BB%9Fi%20h%C3%A0nh%20theo%20gi%E1%BB%9D.png'>

### 4. Thống kê giờ kết thúc của các chuyến tàu

**Biểu đồ cột**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20gi%E1%BB%9D%20k%E1%BA%BFt%20th%C3%BAc%20c%E1%BB%A7a%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u.png'>


**Biểu đồ sao**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/S%E1%BB%91%20l%C6%B0%E1%BB%A3ng%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20k%E1%BA%BFt%20th%C3%BAc%20theo%20gi%E1%BB%9D.png'>


### 5. Thống kê số chuyến tàu của các tháng

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20s%E1%BB%91%20chuy%E1%BA%BFn%20t%C3%A0u%20c%E1%BB%A7a%20c%C3%A1c%20th%C3%A1ng.png'>

### 6. Thống kê thời gian di chuyển của các chuyến tàu

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20th%E1%BB%9Di%20gian%20c%C3%A1c%20chuy%E1%BA%BFn%20t%C3%A0u%20(d%E1%BB%B1a%20tr%C3%AAn%2040k%20quan%20s%C3%A1t).png'>

### 7. Thống kê lượt tàu chạy của các ngày trong tuần

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Th%E1%BB%91ng%20k%C3%AA%20l%C6%B0%E1%BB%A3t%20t%C3%A0u%20c%E1%BB%A7a%20c%C3%A1c%20ng%C3%A0y%20trong%20tu%E1%BA%A7n.png'>

### 8. Lộ trình
Trong dataset có tất cả 62 lộ trình. 

**Biểu đồ tròn thống kê top 20 lộ trình được lựa chọn nhiều nhất theo tỉ lệ phần trăm**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Bi%E1%BB%83u%20%C4%91%E1%BB%93%20top%2020%20l%E1%BB%99%20tr%C3%ACnh%20%C4%91%C6%B0%E1%BB%A3c%20ch%E1%BB%8Dn%20nhi%E1%BB%81u%20nh%E1%BA%A5t.png'>


**Đồ thị cây thống kê top 20 lộ trình được lựa chọn nhiều nhất**

<img src = 'https://github.com/hoangtv2000/data-mining/blob/main/images-spanish-high-speed-rail/Ph%C3%A2n%20t%C3%ADch%20l%E1%BB%99%20tr%C3%ACnh%20b%E1%BA%B1ng%20%C4%91%E1%BB%93%20th%E1%BB%8B%20c%C3%A2y.png'>

