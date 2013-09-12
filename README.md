todolist
========

## Simple todo list v0.2
Link to DEMO [http://weblogic.o3.ua/demo/todolist]

username: test

password: test

## DB for project:

CREATE database ruby:

CREATE TABLE `auth` (
  `id` int(3) unsigned NOT NULL AUTO_INCREMENT,
  `user` tinytext CHARACTER SET utf8 COLLATE utf8_bin NOT NULL,
  `pass` tinytext CHARACTER SET utf8 COLLATE utf8_bin NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8

CREATE TABLE `projects` (
  `id` int(3) unsigned NOT NULL AUTO_INCREMENT,
  `name` tinytext CHARACTER SET utf8 COLLATE utf8_bin NOT NULL,
  `user_id` int(3) unsigned NOT NULL DEFAULT '0',
  `date` date NOT NULL DEFAULT '0000-00-00',
  PRIMARY KEY (`id`),
  FOREIGN KEY (`user_id`) REFERENCES `auth` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

CREATE TABLE `tasks` (
  `id` int(3) unsigned NOT NULL AUTO_INCREMENT,
  `sort_id` int(3) unsigned NOT NULL,
  `name` text CHARACTER SET utf8 COLLATE utf8_bin NOT NULL,
  `status` int(3) unsigned NOT NULL DEFAULT '0',
  `project_id` int(3) unsigned NOT NULL,
  PRIMARY KEY (`id`),
  KEY `project_id` (`project_id`),
  FOREIGN KEY (`project_id`) REFERENCES `projects` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
