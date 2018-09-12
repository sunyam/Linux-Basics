all:
	touch README.txt
	curl -O https://raw.githubusercontent.com/fivethirtyeight/data/master/murder_2016/murder_2015_final.csv
	head -n 1 murder_2015_final.csv > murder_header.csv
	tail -n +2 murder_2015_final.csv > murder_data.csv
	awk -F"," '{ if ($$2 == "Illinois") { print } }' murder_2015_final.csv > murder_illinois.csv
	awk -F"," '{ if ($$2 == "Maryland") { print } }' murder_2015_final.csv | wc -l > murder_maryland.count
	awk -F"," '{ print $$3, $$4 }' murder_illinois.csv > murder_illinois_2014-2015.csv
