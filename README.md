#Code untuk ambil sample

#download data xlsx, simpan ke folder data
wget -P ./data https://github.com/labusiam/dataset/raw/main/weather_data.xlsx

#ubah setiap sheet menjadi file csv tersendiri
in2csv ./data/weather_data.xlsx --sheet "weather_2014" > ./data/weather_2014.csv
in2csv ./data/weather_data.xlsx --sheet "weather_2015" > ./data/weather_2015.csv

#menggabungkan dua buah csv
csvstack ./data/weather_2014.csv ./data/weather_2015.csv > ./data/weather.csv

#menghapus file xlsx
rm ./data/weather_data.xlsx

#mengambil sample dengan rate 0.3
cat ./data/weather.csv | sample -r 0.3 > ./data/sample_weather.csv
