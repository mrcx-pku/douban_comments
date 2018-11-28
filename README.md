# douban_comments
豆瓣电影评论

## 数据集介绍

电影总数：20516

评论总数：4960226（每部电影最多包含500条评论）

具体来说

| 评论的评分    | 评论数目 |
| ------------- | -------- |
| 0（评分保留） | 281211   |
| 1             | 256719   |
| 2             | 493352   |
| 3             | 1499448  |
| 4             | 1573749  |
| 5             | 855747   |

**文件的组织**

评论按照对应的评分位于不同的目录下，每个CSV文件中最多包含300 000条评论。

**数据格式**

CSV文件中的一行数据表示一条评论，格式如下

`movie_id,comment_id,user_id,useful_count,content`

举例

> 1236752834,10551890,49522216,10,全片问题非常多！三观不正：1.儿子血癌晚期马上要死了，居然还有人能放不下工作、没时间陪孩子？2.公司总经理、竞争对手明知道你孩子血癌晚期马上要死了，居然还会死逼你完成业绩、嘲讽你业绩下降？
>
> 1338593082,10551890,47960367,2,这部好电影被埋没了，绝对应该5星8.5以上。只有深深体会过人生悲哀、职场无奈并且已为人父母的人，才能真正明白它在讲什么，并因此而泪流满面，泣不成声。

## 数据读取

你可以这样读取csv中的数据

	import csv
	
	def read_csv(file_name):
	    comments = []
	    comments_append = comments.append
	    with open(file_name, encoding='utf-8', mode='r') as file_in:
	        reader = csv.reader(file_in)
	        for line in reader:
	            if line: comments_append(line)
	    return comments

