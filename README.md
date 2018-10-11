# DylanDunhamCEG4110HW2
Android clock application for CEG4110 HW2
# What this is
This is a simple android application that creates English and Japanese styled clocks that are editable.

# Special Deployment
There is no special deployment.

# Instructions for use:
Below is the main menu. Here you can add clocks by tapping one of the two buttons. The clocks can be adjusted with the drop down select and any changes can be undone with the "undo" button. Changes can be redone as well with the "redo" button.

# Design
The project is made up of 7 classes and 1 interface. It utilizes a model view control to keep the clocks consistant with each other and disallow any one clock from changing the time for all. It also utilizes a command design pattern to allow for undoing and redoing of changes to the model. UML diagram below.

![alt text](https://github.com/dylbo-baggins/DylanDunhamCEG4110HW1/blob/master/SimpleDesignScheme.png)


## MainView Class
#### Variables: timer, tick, ctr, model, cmd, viewStrings
#### Methods: void setHour, void setMin, void setSec, void setWeekday, void setDay, void setYear, void undo, void redo, void newEngClk, void newJapanClk
The MainView class allows for user interaction and controls the events of the application. It requests for clock creation, model changes, and commands to be done and undone. It updates the model every second.
## ClockModel Class
#### Variables: hour, min, sec, weekday, mon, year, ctr
#### Methods: int/void get/setHour, int/void get/setMin, int/void get/setWeekDay, int/void get/setDay, int/void get/setMon, int/void get/setYear
The ClockModel class is the model for the model view controller design that is the source of all the views' info. It is updated through the clkCtr.

## clkCtr Class
#### Variables: model, views, viewStrings
#### Methods: void register, void updateViews, void updateModel, void addView, String getViewAsStrings, List getViewStrings, void tickModel, String getLastClockString
The clkCtr is the controller for the model view controller design. It updates the views and the model.

## clkCmd Class
#### Variables: commandsDone, commandsUndone, ctr, inst
#### Methods: clkCmd getInst, void registerCtr, void doIt, void undoIt, void redoIt
This is the command design patter class of the project. It saves user clock edits on two different stacks for them to be undone or redone. 

## clkStack Class
#### Variables: stack
#### Methods: void push, int[] pop, int[] peek, int getSize
The clkStack is a specialized stack to hold the 7 integer variables that constitute a clkView. It holds the integers in an int array that is in an int array ArrayList.

## clkView Interface
#### Methods: void setHour, void setMin, void setSec, void setDay, void setWeekday, void setMon, void setYear, void getTime
The clkView is an interface so the different clkViews can be consistant and kept in the same array list.

## engClock Class
#### Variables: hour, min, sec, weekday, day, mon, year
#### Methods: void setHour, void setMin, void setSec, void setDay, void setWeekday, void setMon, void setYear, void getTime
The engClock class extends clkView. It represents an instance of a clock using traditional western time keeping. It is updated from the controller for the model controller design.

## japanClock Class
#### Variables: hour, min, sec, weekday, day, mon, year
#### Methods: void setHour, void setMin, void setSec, void setDay, void setWeekday, void setMon, void setYear, void getTime
The japanClock class extends clkView. It represents an instance of a clock using traditional Japanese time keeping. It is updated from the controller for the model controller design.
