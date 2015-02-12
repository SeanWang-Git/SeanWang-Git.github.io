---
layout: post
title: Shell-case-esac
---

#### case-in 

	case ... esac 与其他语言中的 switch ... case 语句类似，是一种多分枝选择结构。
	
	case 语句匹配一个值或一个模式，如果匹配成功，执行相匹配的命令。case语句格式如下：
	case 值 in
	模式1)
	    command1
	    command2
	    command3
	    ;;
	模式2）
	    command1
	    command2
	    command3
	    ;;
	*)
	    command1
	    command2
	    command3
	    ;;
	esac

	#!/bin/bash

	option=$1

	case ${option} in
	        1)
	                echo 1
	        ;;
	        2)
	                echo 2
	        ;;
	        3)
	                echo 3
	        ;;
	        *)
	                echo 4
	        ;;
	esac