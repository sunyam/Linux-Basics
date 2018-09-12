#russ=$(shell awk -F"\t" '{ if ($$3 == "ru") { print } }' book_tweets.tsv | wc -l)
#aug=$(shell awk -F"\t" '{ if ($$2 ~ "Aug .* 2016") { print } }' book_tweets.tsv | wc -l)
#retweets=$(shell awk -F"\t" '{ if ($$4 ~ "^RT") { print } }' book_tweets.tsv | wc -l)
#got=$(shell awk -F"\t" '{ if ($$4 ~ "#gameofthrones") { print } }' book_tweets.tsv | wc -l)


download:
	mkdir -p data
	curl -o ./data/books_tweets100000.txt.gz www.derekruths.com/static/reading_tweets/books_tweets100000.txt.gz

prep:
	gunzip ./data/books_tweets100000.txt.gz
	cat ./data/books_tweets100000.txt | jq -r '. |  [.user.id, .created_at, .user.lang, .text] | @tsv' > book_tweets.tsv
	awk -F"\t" '{ if ($$2 ~ "Oct 23 .* 2012") { print } }' book_tweets.tsv > tweetsOct2012.tsv
	awk -F"\t" '{ if ($$4 ~ "#gameofthrones") { print } }' book_tweets.tsv > tweets_got.tsv

analyze:
	touch results.txt
	echo "Number of tweets in Russian: $(shell awk -F"\t" '{ if ($$3 == "ru") { print } }' book_tweets.tsv | wc -l)" >> results.txt
	echo "Number of tweets from Aug 2016: $(shell awk -F"\t" '{ if ($$2 ~ "Aug .* 2016") { print } }' book_tweets.tsv | wc -l)" >> results.txt
	echo "Retweets: $(shell awk -F"\t" '{ if ($$4 ~ "^RT") { print } }' book_tweets.tsv | wc -l)" >> results.txt
	echo "GOT: $(shell awk -F"\t" '{ if ($$4 ~ "#gameofthrones") { print } }' book_tweets.tsv | wc -l)" >> results.txt
