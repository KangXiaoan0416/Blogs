---
title: swing
date: 2018-04-08 19:46:21
tags: java,swing
categories: Java图形
---
### Swing组件的层次结构
类型：　顶层组件，中间组件，基本组件
1. 顶层容器：JFrame,JApplet,JDialog,JWindow,即Window组件，可独立显示
2. 中间容器：JPanel,JScrollPane,JSplitPane,JToolBar,基本控件的载体，不能独立显示
3. 特殊容器：在GUI上起特殊作用的中间层，如JInternalFrame, JLayeredPane,JRootPane(中间容器的一种，不过更能起到美化和专业化的作用)
4. 基本组件：基本组件是要依托容器才能显示的组件，不能独立存在．JButton,JComboBox,JList,JMenu,JSlider,JTextField
