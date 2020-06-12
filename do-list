
#!/bin/bash

if ! [ -d /home/$USER/.do-list ];then

	mkdir /home/$USER/.do-list
fi

Usage(){

	echo Usage: do_list [options] [command]
	echo "A Todo list for linuxer by using typora" 
	echo Author: nj-jay
	echo email: nj@nj-jay.com
	echo Options:
	echo "	不加选项:写今天的do-list"
	echo "	-a: 查看所有的do-list"
	echo "	-y: 查看昨天的do-list"
	echo "	-t: 写明天的do-list"
	echo "	-d: 写指定日期的do-list "
	echo "		格式要求 05.20 表示5月20号"
	echo "	默认的目录是~/.do-list"
}
Yesterday(){
	month1=$(date -d"yesterday" | awk '{print $2}' | awk 'gsub(/[^[:digit:]]/," ",$0)')
	month2=$(date -d"yesterday" | awk '{print $2}')
	day=$(date -d"yesterday" | awk '{print $3}' | awk 'gsub(/[^[:digit:]]/," ",$0)')
	date="$month1.$day.md"
	dateFin=$(echo $date | sed 's/ //g')
	if ! [ -f /home/$USER/.do-list/$month2/$dateFin ];then
    		mkdir -p /home/$USER/.do-list/$month2/
    		touch  /home/$USER/.do-list/$month2/$dateFin
	fi
	if [ -f /usr/bin/typora ];then
		nohup typora  /home/$USER/.do-list/$month2/$dateFin &>/dev/null &
		else
			vim  /home/$USER/.do-list/$month2/$dateFin
	fi
}

Today(){
	#获取今天的日期
	month1=$(date | awk '{print $2}' | awk 'gsub(/[^[:digit:]]/," ",$0)')
	month2=$(date | awk '{print $2}')
	day=$(date | awk '{print $3}' | awk 'gsub(/[^[:digit:]]/," ",$0)')
	date="$month1.$day.md"
	dateFin=$(echo $date | sed 's/ //g')
	if ! [ -f ~/notes/do_list/$month2/$dateFin ];then
    		mkdir /home/$USER/.do-list/$month2/
    		touch /home/$USER/.do-list/$month2/$dateFin
	fi
	
	if [ -f /usr/bin/typora ];then
		nohup typora /home/$USER/.do-list/$month2/$dateFin &>/dev/null &
		else
			vim /home/$USER/.do-list/$month2/$dateFin
	fi
	
	
}

Tomorrow(){
	month1=$(date -d"tomorrow" | awk '{print $2}' | awk 'gsub(/[^[:digit:]]/," ",$0)')
	month2=$(date -d"tomorrow" | awk '{print $2}')
	day=$(date -d"tomorrow" | awk '{print $3}' | awk 'gsub(/[^[:digit:]]/," ",$0)')
	date="$month1.$day.md"
	dateFin=$(echo $date | sed 's/ //g')
	if ! [ -f /home/$USER/.do-list/$month2/$dateFin ];then
    		mkdir -p /home/$USER/.do-list/$month2/
    		touch /home/$USER/.do-list/$month2/$dateFin
	fi
	if [ -f /usr/bin/typora ];then
		nohup typora /home/$USER/.do-list/$month2/$dateFin &>/dev/null &
		else
			vim /home/$USER/.do-list/$month2/$dateFin
	fi
}

All(){
	
	if [ -f /usr/bin/typora ];then
		nohup typora /home/$USER/.do-list &>/dev/null &
		else
			vim /home/$USER/.do-list
	fi
}



Test(){

	while getopts "atyhd:" opt
	do
		case $opt in
			a)
			All
			;;
			t)
			Tomorrow
			;;
			y)
			Yesterday
			;;
			d)
			date=$OPTARG
			
			month=$(echo $date | cut -d '.' -f 1)
			echo $day
			if ! [ -f /home/$USER/.do-list/$month月/$date.md ];then
    				mkdir -p /home/$USER/.do-list/$month月/
    				touch /home/$USER/.do-list/$month月/$date.md
			fi
			if [ -f /usr/bin/typora ];then
				nohup typora /home/$USER/.do-list/$month月/$date.md &>/dev/null &
				else
					vim /home/$USER/.do-list/$month月/$date.md
			fi
			;;
			h)
			Usage
			;;
			?)
			echo unknow options
			Usage
			exit;;
		esac
	done
}

main(){
	[ $# -lt 1 ] && {
		Today
		exit 0
	}
	Test $*
}

main $*
