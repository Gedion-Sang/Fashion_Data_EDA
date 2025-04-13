# **FASHION DATA EXPLORATORY DATA ANALYSIS PROJECT**


## *Project Overview.*

- *`Problem Statement and Objectives`*

The goal of the project is to perform an analysis of the data provided and from it derive key insights about the data.

- *`Tools Used`*

Here we will be using PostgreSQL for data exploration and Python(Pandas,Numpy,Seaborn,Matplotlib) for creating visualizations.

- *`Learning Objectives`*

1. Use SQL to extract, aggregate, and analyze data.
2. Develop business insights from transactional datasets.
3. Present findings in a professional PowerPoint presentation.


#### Step 1: Import and Explore the Database

> Import the fashion.sql file into your SQL database (e.g., MySQL, PostgreSQL).

To import the data into the database we first have to create the table using the `CREATE` function and then we insert the data using the `INSERT`function.
```sql
CREATE TABLE fashion (
	clothing_type VARCHAR(8),
	category VARCHAR(11),
	price DECIMAL(5,2),
	discount DECIMAL(4,2),
	shop_outlet VARCHAR(50),
	delivery_date DATE,
	order_date DATE,
	revenue DECIMAL(7,2),
	customer_name VARCHAR(50),
	customer_email VARCHAR(50)
);

INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'accessories', 113.84, 6.15, 'Photobug', '6/20/2022', '8/6/2023', 1102.01, 'Alfy Piborn', 'apiborn0@squarespace.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'accessories', 60.62, 49.47, 'Jetwire', '2/6/2024', '1/1/2022', 5521.65, 'Demetra Stutely', 'dstutely1@wired.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shirts', 119.19, 41.14, 'Edgewire', '6/3/2022', '11/14/2022', 7252.86, 'Giselle Ruegg', 'gruegg2@weebly.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shoes', 43.19, 12.5, 'Twitterbridge', '11/19/2022', '8/1/2024', 4866.12, 'Sven Loughlin', 'sloughlin3@surveymonkey.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 116.46, 28.74, 'Zoomlounge', '12/17/2024', '1/29/2024', 2009.4, 'Cesya Boustead', 'cboustead4@nps.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 154.12, 15.71, 'Shufflebeat', '3/24/2023', '1/3/2022', 4343.05, 'Rollo Beiderbecke', 'rbeiderbecke5@upenn.edu');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shirts', 197.72, 4.93, 'Gigaclub', '3/28/2024', '3/17/2022', 3365.54, 'Anna-maria Milliere', 'amilliere6@weibo.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'pants', 76.62, 8.44, 'Tazz', '3/1/2025', '7/17/2024', 1906.1, 'Leeann Dossett', 'ldossett7@omniture.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'pants', 139.8, 6.76, 'Mycat', '8/7/2024', '10/1/2022', 3735.92, 'Idalina Klimas', 'iklimas8@wiley.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'accessories', 137.37, 13.81, 'Zoomdog', '5/17/2022', '6/1/2023', 6348.41, 'Dorothy Alfonsini', 'dalfonsini9@youtu.be');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'accessories', 62.52, 26.63, 'Feedbug', '5/10/2023', '11/14/2022', 7900.39, 'Charmaine Swatridge', 'cswatridgea@mozilla.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shoes', 185.96, 0.9, 'Skimia', '1/31/2025', '2/16/2023', 1971.21, 'Palmer Hoggin', 'phogginb@cpanel.net');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 41.56, 19.18, 'Thoughtstorm', '4/26/2022', '12/26/2022', 6860.26, 'Jeffry Cuff', 'jcuffc@scribd.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shoes', 56.09, 12.11, 'Eare', '11/30/2024', '4/18/2022', 4574.48, 'Kerrin Dickons', 'kdickonsd@cyberchimps.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 93.37, 20.07, 'Midel', '9/26/2022', '2/24/2024', 9793.02, 'Laughton Menendez', 'lmenendeze@kickstarter.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'dresses', 78.27, 0.49, 'Feedbug', '12/18/2022', '5/12/2023', 6874.89, 'Corrina Greensted', 'cgreenstedf@salon.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shoes', 56.5, 24.58, 'Ntags', '3/7/2023', '3/11/2023', 5003.36, 'Bel Oluwatoyin', 'boluwatoying@bbb.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 189.63, 44.66, 'Oba', '10/15/2022', '4/23/2022', 9455.11, 'Crystal Fulleylove', 'cfulleyloveh@creativecommons.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'dresses', 93.89, 11.03, 'Teklist', '6/26/2022', '11/29/2023', 579.59, 'Chaunce Sporrij', 'csporriji@360.cn');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shirts', 125.06, 29.45, 'Jaxspan', '3/2/2022', '3/27/2023', 5026.23, 'Kalila Charopen', 'kcharopenj@sakura.ne.jp');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'dresses', 157.63, 45.62, 'Twinte', '11/12/2023', '3/12/2025', 2966.23, 'Tymothy Sexton', 'tsextonk@barnesandnoble.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'dresses', 183.49, 25.14, 'Youspan', '7/1/2022', '11/22/2023', 8723.35, 'Cord Hoodspeth', 'choodspethl@state.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'accessories', 21.91, 45.58, 'Tavu', '2/9/2023', '1/22/2022', 8728.01, 'Bonnie Halfhead', 'bhalfheadm@google.it');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 108.7, 40.46, 'Babbleopia', '8/3/2024', '10/10/2022', 3004.62, 'Corey Robus', 'crobusn@army.mil');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'dresses', 131.43, 22.42, 'Yodo', '4/19/2022', '10/16/2023', 7457.31, 'Levin Lubbock', 'llubbocko@marketwatch.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'pants', 68.31, 7.59, 'Divavu', '6/11/2022', '3/24/2025', 3959.59, 'Jeno Leonard', 'jleonardp@bloomberg.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 161.26, 44.2, 'Eadel', '9/22/2022', '7/12/2024', 9163.15, 'Obadias Rathmell', 'orathmellq@photobucket.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'accessories', 49.77, 24.83, 'Teklist', '3/27/2025', '6/9/2024', 9139.56, 'Elwira Duckett', 'educkettr@wikispaces.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'accessories', 194.37, 31.86, 'Yamia', '2/20/2023', '6/22/2023', 5171.8, 'Brod Sugarman', 'bsugarmans@ifeng.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 53.8, 24.16, 'Realcube', '4/19/2022', '1/5/2023', 5798.22, 'Tandie Frances', 'tfrancest@fc2.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shirts', 69.6, 13.51, 'Skyvu', '4/28/2022', '10/31/2024', 2647.25, 'Devon Niese', 'dnieseu@qq.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'dresses', 111.95, 36.99, 'Flipstorm', '2/24/2022', '9/8/2023', 5255.26, 'Pyotr Lemanu', 'plemanuv@prlog.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'dresses', 64.63, 4.64, 'Tazz', '11/23/2022', '3/8/2025', 1477.89, 'Serge Linger', 'slingerw@usgs.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shoes', 173.52, 49.76, 'Topicstorm', '10/2/2023', '8/20/2023', 4265.66, 'Valaree Denizet', 'vdenizetx@fastcompany.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 124.09, 49.51, 'Kare', '6/23/2024', '1/19/2024', 5735.45, 'Elwira Kirman', 'ekirmany@elpais.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 155.1, 20.53, 'Brightdog', '6/24/2022', '6/7/2023', 8435.52, 'Myriam Itzchaky', 'mitzchakyz@vistaprint.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'dresses', 136.31, 37.45, 'Vidoo', '8/2/2022', '10/25/2023', 1894.25, 'Daryn Spellard', 'dspellard10@ebay.co.uk');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shoes', 56.17, 22.99, 'Skippad', '12/22/2024', '1/14/2022', 2606.06, 'Earlie Haskett', 'ehaskett11@jalbum.net');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 127.61, 7.94, 'Flashpoint', '2/4/2024', '10/8/2023', 5366.63, 'Ardelis Hardesty', 'ahardesty12@sourceforge.net');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'dresses', 23.18, 13.7, 'Dynazzy', '10/5/2022', '9/16/2022', 8873.5, 'Gibby Jachimczak', 'gjachimczak13@google.cn');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shoes', 66.46, 35.41, 'Trunyx', '2/25/2022', '3/10/2024', 2344.62, 'King Drysdall', 'kdrysdall14@taobao.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shirts', 73.1, 31.72, 'Yakitri', '3/26/2023', '2/26/2024', 1638.59, 'Julia Durnin', 'jdurnin15@usa.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'accessories', 96.72, 19.0, 'Jatri', '10/20/2023', '3/8/2022', 4256.99, 'Judas Hunstone', 'jhunstone16@free.fr');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'accessories', 47.06, 47.4, 'Dynava', '2/21/2025', '11/4/2023', 249.27, 'Anderea Demchen', 'ademchen17@weibo.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shoes', 93.04, 29.6, 'Mymm', '7/28/2022', '1/23/2023', 8341.79, 'Shirley Denge', 'sdenge18@admin.ch');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shoes', 124.25, 14.35, 'Mydeo', '2/19/2025', '4/8/2022', 2816.04, 'Irma O'' Mullan', 'io19@chicagotribune.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'pants', 79.46, 25.46, 'Dabshots', '4/16/2024', '10/12/2023', 6326.67, 'Leonardo Wycherley', 'lwycherley1a@creativecommons.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 24.73, 40.91, 'Brightbean', '5/9/2022', '5/10/2024', 9926.56, 'Brennen Lambirth', 'blambirth1b@amazonaws.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shirts', 171.9, 43.21, 'Rhynyx', '4/3/2023', '2/6/2023', 6206.91, 'Bram Peery', 'bpeery1c@latimes.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shoes', 116.71, 10.13, 'Jayo', '5/6/2022', '3/2/2022', 9721.78, 'Kassey Smidmore', 'ksmidmore1d@webeden.co.uk');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shoes', 47.21, 40.54, 'Trupe', '8/18/2022', '4/23/2023', 8999.59, 'Jere Headley', 'jheadley1e@devhub.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'pants', 55.84, 32.74, 'Kwinu', '1/7/2025', '4/15/2024', 6243.83, 'Floris Di Dello', 'fdi1f@dropbox.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'accessories', 177.92, 10.34, 'Avamba', '9/28/2022', '2/26/2022', 1737.56, 'Cozmo Kibel', 'ckibel1g@networksolutions.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'dresses', 173.35, 3.04, 'Skalith', '8/21/2022', '11/17/2023', 2302.05, 'Jacynth Brozek', 'jbrozek1h@ow.ly');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 122.0, 30.15, 'Pixonyx', '10/22/2022', '4/13/2023', 2836.33, 'Dehlia Haggus', 'dhaggus1i@ning.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'accessories', 197.91, 28.39, 'Oodoo', '5/24/2023', '9/29/2022', 6247.29, 'Sterne Coppenhall', 'scoppenhall1j@google.com.au');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'pants', 30.11, 45.31, 'Devbug', '2/12/2025', '5/7/2022', 5992.37, 'Reamonn Sloane', 'rsloane1k@archive.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 43.21, 16.35, 'Edgeify', '9/7/2024', '5/21/2024', 3227.99, 'Leeann Thickens', 'lthickens1l@umich.edu');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 187.42, 30.81, 'Yombu', '3/1/2022', '9/2/2022', 1639.94, 'Rickie Giraldez', 'rgiraldez1m@cpanel.net');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 140.17, 2.24, 'Vipe', '3/26/2024', '5/27/2023', 4191.4, 'Justinian Renol', 'jrenol1n@elpais.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'dresses', 177.53, 11.33, 'Topicstorm', '5/24/2022', '10/2/2024', 9308.51, 'Ad Nutbeem', 'anutbeem1o@ustream.tv');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shirts', 52.49, 41.69, 'Bubblebox', '3/8/2025', '10/13/2024', 9262.05, 'Thoma Durker', 'tdurker1p@furl.net');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shirts', 73.88, 37.34, 'Meevee', '3/7/2023', '4/16/2023', 6496.66, 'Shane Reis', 'sreis1q@gov.uk');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'pants', 103.56, 13.67, 'Demizz', '11/21/2024', '10/14/2023', 3975.7, 'Cynthy Wolverson', 'cwolverson1r@domainmarket.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 123.34, 43.74, 'Abatz', '5/19/2024', '5/29/2022', 9064.04, 'Hans Heighway', 'hheighway1s@elegantthemes.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'dresses', 33.2, 12.65, 'Tazzy', '2/24/2025', '10/2/2022', 4624.02, 'Agretha Pautard', 'apautard1t@drupal.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 103.35, 30.41, 'Snaptags', '6/26/2024', '6/24/2024', 1664.57, 'Carny Jessup', 'cjessup1u@accuweather.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'pants', 102.98, 0.94, 'Wordify', '3/25/2022', '9/8/2023', 9096.07, 'Karna Dadswell', 'kdadswell1v@youtu.be');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 62.48, 30.43, 'Podcat', '8/10/2023', '8/19/2024', 3509.29, 'Tirrell Vanelli', 'tvanelli1w@whitehouse.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shirts', 141.09, 12.18, 'Wikido', '6/3/2024', '12/23/2024', 2284.11, 'Terrell Pybworth', 'tpybworth1x@123-reg.co.uk');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'pants', 145.01, 34.9, 'Livetube', '11/23/2022', '11/3/2024', 9780.81, 'Ursola Petrishchev', 'upetrishchev1y@epa.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 65.31, 12.95, 'Snaptags', '2/25/2025', '1/21/2023', 6390.18, 'Casi Jina', 'cjina1z@narod.ru');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shirts', 152.36, 8.7, 'Eare', '10/23/2023', '4/26/2023', 6124.97, 'Gabe Shekle', 'gshekle20@bandcamp.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'dresses', 137.54, 15.41, 'Mynte', '7/1/2024', '10/27/2023', 6024.69, 'Birgitta Tawn', 'btawn21@mediafire.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'accessories', 32.45, 18.54, 'Twitterwire', '8/1/2023', '5/4/2024', 5126.73, 'Gray Sunman', 'gsunman22@indiatimes.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 169.91, 25.87, 'Jaxspan', '9/30/2022', '3/26/2024', 3098.87, 'Katharine Scoggan', 'kscoggan23@netscape.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'accessories', 12.57, 4.3, 'Yodo', '7/9/2022', '10/6/2023', 9244.44, 'Alberik Congreave', 'acongreave24@deliciousdays.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'dresses', 135.47, 46.92, 'Divanoodle', '11/29/2024', '6/6/2023', 1791.27, 'Mitchel Ogles', 'mogles25@adobe.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shirts', 102.82, 38.32, 'Brightbean', '3/9/2022', '2/10/2023', 2685.31, 'Marlin Crittal', 'mcrittal26@nasa.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'pants', 58.18, 37.07, 'Browsebug', '7/11/2024', '12/10/2022', 1544.61, 'Aguie Janatka', 'ajanatka27@biblegateway.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'dresses', 188.39, 47.28, 'Latz', '4/5/2022', '9/12/2023', 4181.68, 'Vassily Conring', 'vconring28@walmart.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 186.16, 49.88, 'Photospace', '2/4/2023', '11/27/2022', 401.4, 'Terri Gritten', 'tgritten29@google.cn');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shoes', 92.88, 20.9, 'Browsebug', '1/14/2024', '12/5/2022', 1362.82, 'Leesa Tribe', 'ltribe2a@oaic.gov.au');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shoes', 120.13, 5.17, 'Tagopia', '8/1/2024', '4/1/2022', 9520.43, 'Ricky Jeandon', 'rjeandon2b@baidu.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 48.35, 31.69, 'Oyonder', '5/27/2023', '6/15/2023', 8603.05, 'Antin Walicki', 'awalicki2c@vkontakte.ru');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'pants', 13.42, 12.69, 'Oodoo', '6/1/2023', '9/23/2022', 1448.99, 'Prissie Turtle', 'pturtle2d@chronoengine.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shirts', 77.72, 6.5, 'Meedoo', '5/18/2022', '6/11/2024', 776.29, 'Danie Zupa', 'dzupa2e@shop-pro.jp');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 164.54, 43.74, 'Trilith', '3/9/2025', '4/25/2023', 9993.83, 'Shaughn Greenwood', 'sgreenwood2f@theatlantic.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 72.03, 11.79, 'Voomm', '4/26/2023', '1/5/2023', 2900.08, 'Magdaia Allcock', 'mallcock2g@slideshare.net');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 177.08, 21.7, 'Yoveo', '8/21/2023', '1/28/2022', 8709.0, 'Otho Yarr', 'oyarr2h@baidu.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'dresses', 42.69, 28.85, 'Eadel', '7/9/2023', '1/14/2024', 754.06, 'Rora Whordley', 'rwhordley2i@drupal.org');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'dresses', 199.74, 16.8, 'Innotype', '5/10/2023', '9/19/2023', 1055.81, 'Isa Wainwright', 'iwainwright2j@bing.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shirts', 109.16, 10.66, 'Fivebridge', '2/4/2023', '9/13/2024', 9746.98, 'Salvatore Dommersen', 'sdommersen2k@biblegateway.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'dresses', 112.58, 4.96, 'Linklinks', '1/6/2023', '6/11/2023', 1672.06, 'Rollie Hallibone', 'rhallibone2l@home.pl');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'dresses', 134.15, 7.57, 'Brightbean', '5/17/2023', '12/20/2022', 366.35, 'Sunny Veness', 'sveness2m@foxnews.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 108.38, 5.82, 'Rhybox', '8/31/2024', '1/1/2023', 5215.14, 'Vinni Rasch', 'vrasch2n@wunderground.com');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('men', 'shirts', 188.96, 17.87, 'Skimia', '11/23/2023', '4/14/2022', 4898.09, 'Hazel Pinching', 'hpinching2o@si.edu');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'accessories', 11.88, 38.74, 'Kimia', '3/13/2022', '6/15/2023', 3527.45, 'Rancell Cristofari', 'rcristofari2p@fda.gov');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('children', 'shoes', 141.65, 35.04, 'Flipbug', '3/13/2022', '1/11/2025', 2663.98, 'Beulah Pawfoot', 'bpawfoot2q@amazon.de');
INSERT INTO fashion (clothing_type, category, price, discount, shop_outlet, delivery_date, order_date, revenue, customer_name, customer_email) VALUES ('women', 'shirts', 169.94, 10.59, 'Dynabox', '4/27/2024', '7/15/2022', 7064.56, 'Cordelie Caitlin', 'ccaitlin2r@thetimes.co.uk');

```

## Use the following commands to understand the structure:

""
SHOW TABLES;

To show tables we use `SELECT` function. The asterisk `*` represents all. The SQL code below can be read as `select all from the schema fashion which contains the table fashion`.

```sql
SELECT * FROM fashion.fashion;
```

#### Step 2: Perform the Following Analysis

A. Sales Analysis

1. Identify the top 5 selling products.

To identify top products we add up the total revenue from the sales.We then group by the category and limit our results by 5 to achieve the expected result of the top 5 products.
```sql
SELECT category, SUM(revenue) AS "Total Revenue"
FROM fashion.fashion
GROUP BY category 
ORDER BY "Total Revenue" DESC 
LIMIT 5;

```
2. Determine the monthly trend of total sales.

To determine the monthly trend we first have to extract the month and year for easier categorization, we then sum the revenue and count all rows as the total orders.  
`TO_CHAR` keyword extracts the year-month-date as an argument value while the `EXTRACT` keyword returns a float value.
```sql
SELECT 
    TO_CHAR(order_date, 'YYYY-MM') AS "Year_Month",
    SUM(revenue) AS "Total Revenue",
    COUNT(*) AS "Total Orders"
FROM fashion.fashion
GROUP BY "Year_Month"
ORDER BY "Year_Month";
```
3. Analyze sales distribution by day of the week.

Extract day of the week from order_date and then we perform aggregate functions on our key metrics to find the total sales.
```sql
SELECT
	 TO_CHAR(order_date, 'Day') AS "Day of the Week",
	 COUNT(*) AS "Total Orders",
	 SUM(revenue) "Total Revenue"
FROM fashion.fashion
GROUP BY "Day of the Week"
ORDER BY "Total Revenue"  DESC;
```
B. Customer Insights

1. List the top 10 customers by revenue.

Identify the customers who generated the most revenue
```sql
SELECT customer_name, revenue
FROM fashion.fashion
ORDER BY revenue DESC
LIMIT 10;
```
2. Compare the number of repeat vs new customers.

To identify repeat and new customers, we first have to create a temporary result set or a CTE using the `WITH` function,we then use the `CASE` function to add a categorization of the data.
```sql
WITH customer_frequency AS (
    SELECT 
        customer_email,
        COUNT(*) AS Orders
    FROM fashion
    GROUP BY customer_email
)
SELECT 
    CASE 
        WHEN Orders = 1 THEN 'New Customers'
        ELSE 'Repeat Customers'
    END AS customer_type,
    COUNT(*) AS "Total Customers",
    SUM(Orders) AS "Order Total"
FROM customer_frequency 
GROUP BY customer_type;
```
3. Identify locations with most active buyers (if applicable).

To identify the most active shop outlet we get all the total orders from the dataset and then order by the number of orders madeto identify the most active outlet.
```sql
SELECT shop_outlet, COUNT(*) "Total Orders"
FROM fashion.fashion
GROUP BY shop_outlet 
ORDER BY "Total Orders" desc
limit 5;
```
C. Time-Based Analysis

1. Compare sales between weekdays and weekends.

The `CASE` function is once again used to extract the day of the week.`NOT IN` function is a negation of the `IN` function both of which are used to specify a list of matches,here the functions are used to categorize the days of the week based on index, i.e. index 0 represents Sunday, while index 6 represents Saturday hence a weekend otherwise indexes 1-5 reprsent weekdays.
```sql
SELECT 
    CASE 
        WHEN EXTRACT(DOW FROM order_date) NOT IN (0, 6) THEN 'Weekday'
        ELSE 'Weekend'
    END AS day_type,
    SUM(revenue) AS "Total Revenue",
    COUNT(*) AS "Total Orders"
FROM fashion
GROUP BY day_type;
```
2. Find peak shopping hours (if timestamp is available).

To identify the hours we had to extract the `HOUR` from the timestamp. A timestamp was not provided and we therefore could not extract it. However, if a timestamp had been provided we could use the SQL code below(PostgresSQL) to extract the hour 
```sql
SELECT EXTRACT(HOUR FROM order_date)FROM fashion.fashion;
```
D. Inventory Insights

The double pipe `||` is used to concatenate or consolidate different fields and data types into a single field. Here we used a combination of the double pipe and a string operator `-` usually enclosed in single quotation marks. The concatenate function `|| '-' ||` here is used to combine the fields clothing_type and category as a single field.

1. Identify low stock items.

```sql
SELECT 
    clothing_type || ' - ' || category AS "Item",
    COUNT(*) AS "Stock count"
FROM fashion.fashion
GROUP BY "Item" 
ORDER BY "Stock count"  ASC
LIMIT 5;
```
2. Find items that are frequently restocked.
```sql
SELECT 
    clothing_type || ' - ' || category AS items,
    COUNT(*) AS frequently_restocked
FROM fashion
GROUP BY items
ORDER BY frequently_restocked DESC
LIMIT 5;
```
E. Custom Question

1. Formulate one additional interesting question and answer it using SQL.
```sql

```

### Deliverables
#### Group Work

Work in groups of 2–4 students.

Written Report
Submit a github repo that includes:

1. A brief explanation for each question
2. The SQL query used
3. Result tables or charts

### PowerPoint Presentation

> Create a PowerPoint with a maximum of 8 slides:

1. Title slide (Group name, members)
2. Problem statement & objectives
3. Key findings (charts + interpretations)
4. Custom question results
5. Summary & business recommendations

