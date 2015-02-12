---
layout: post
title: Shell-if-else
---

#### if

	if [ expression ]
	then
		echo 'sth'
	fi

#### if-else

	if [ expression ]
	then
		echo 'sth'
	else
		echo 'sth'
	fi

#### if-elif-else

	if [ expression ]
	then
		echo 'sth'
	elif [ expression ]
	then	
		echo 'sth'
	else
		echo 'sth'
	fi
	
#### test 函数

	if test expression
	then
		echo 'sth'
	elif test expression
	then
		echo 'sth'
	else
		echo 'sth'
	fi