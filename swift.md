1.Marks Card


var Course="BCA Game & App Development"
var studentName=""
var regNumber=""

//theory subs
var subjectOne=[67,67,67]
var subjectTwo=[67,67,67]


//practical subs
var subjectThree=[67,67,67]
var subjectFour=[67,67,67]
var subjectFive=[67,67,67]

//grade array
var gradeArray=[Int](repeating: 0, count: 5)
var actualGrade=[String](repeating: "a", count: 5)



func handleStudentInput()
{
    print("enter the student name")
    studentName=readLine()!
    print("enter student register number")
    regNumber=readLine()!
}
func handleSubjectInput()
{
    //sub1
    //cce =30
    while subjectOne[0]<0||subjectOne[0]>30
    {
        print("enter CCE marks for Disaster management")
        subjectOne[0]=(Int)(readLine()!)!
    }
    //iat=20
    while subjectOne[1]<0||subjectOne[1]>20
    {
        print("enter IAT marks for Disaster management")
        subjectOne[1]=(Int)(readLine()!)!
    }
    //TEE=50
    while subjectOne[2]<0||subjectOne[2]>50
    {
        print("enter TEE marks for Disaster management")
        subjectOne[2]=(Int)(readLine()!)!
    }
    
    //sub2
    //cce=30
    while subjectTwo[0]<0||subjectTwo[0]>30
    {
        print("enter CCE marks for Software Engineering")
        subjectTwo[0]=(Int)(readLine()!)!
    }
    //iat=20
    while subjectTwo[1]<0||subjectTwo[1]>20
    {
        print("enter IAT marks for Software Engineering")
        subjectTwo[1]=(Int)(readLine()!)!
    }
    //TEE=50
    while subjectTwo[2]<0||subjectTwo[2]>50
    {
        print("enter TEE marks for Software Engineering")
        subjectTwo[2]=(Int)(readLine()!)!
    }
    //sub3
    //cce=30
    while subjectThree[0]<0||subjectThree[0]>30
    {
        print("enter CCE marks for C#")
        subjectThree[0]=(Int)(readLine()!)!
    }
    //sub4
    //iat=20
    while subjectThree[1]<0||subjectThree[1]>20
    {
        print("enter IAT marks for C#")
        subjectThree[1]=(Int)(readLine()!)!
    }
    //TEE=50
    while subjectThree[2]<0||subjectThree[2]>50
    {
        print("enter TEE marks for C#")
        subjectThree[2]=(Int)(readLine()!)!
    }
    //sub 4
    //CCE=30
    while subjectFour[0]<0||subjectFour[0]>30
    {
        print("enter CCE marks for C++")
        subjectFour[0]=(Int)(readLine()!)!
    }
    //iat=20
    while subjectFour[1]<0||subjectFour[1]>20
    {
        print("enter IAT marks for C++")
        subjectFour[1]=(Int)(readLine()!)!
    }
    //TEE=50
    while subjectFour[2]<0||subjectFour[2]>50
    {
        print("enter TEE marks for C++")
        subjectFour[2]=(Int)(readLine()!)!
    }
    //sub 5
    //CCE=30
    while subjectFive[0]<0||subjectFive[0]>30
    {
        print("enter CCE marks for Java")
        subjectFive[0]=(Int)(readLine()!)!
    }
    //iat=20
    while subjectFive[1]<0||subjectFive[1]>20
    {
        print("enter IAT marks for Java")
        subjectFive[1]=(Int)(readLine()!)!
    }
    //TEE=50
    while subjectFive[2]<0||subjectFive[2]>50
    {
        print("enter TEE marks for Java")
        subjectFive[2]=(Int)(readLine()!)!
    }
}

func gradeMethod()
{
    gradeArray[0]=subjectOne[0]+subjectOne[1]+subjectOne[2];
    gradeArray[1]=subjectTwo[0]+subjectTwo[1]+subjectTwo[2];
    gradeArray[2]=subjectThree[0]+subjectThree[1]+subjectThree[2];
    gradeArray[3]=subjectFour[0]+subjectFour[1]+subjectFour[2];
    gradeArray[4]=subjectFive[0]+subjectFive[1]+subjectFive[2];
    
    for gradeIndex in 0...4
    {
        switch gradeArray[gradeIndex]
        {
        case 100:
            actualGrade[gradeIndex]="O"
        case 95...99:
            actualGrade[gradeIndex]="A+"
        case 90...94:
            actualGrade[gradeIndex]="A"
        case 80...89:
            actualGrade[gradeIndex]="B+"
        case 75...79:
            actualGrade[gradeIndex]="B"
        case 70...74:
            actualGrade[gradeIndex]="C+"
        case 66...69:
            actualGrade[gradeIndex]="C"
        case 55...65:
            actualGrade[gradeIndex]="D"
        case 40...54:
            actualGrade[gradeIndex]="P"
        case 0...39:
            actualGrade[gradeIndex]="F"
        default:
            print("Invalid Marks")
        }
    }
}

func printMarksCard()
{
    print("                      CMR UNIVERSITY")
    print("Course:",Course,"                 SEM:1")
    print("Reg No.",regNumber)
    print("Name:",studentName)
    print("Subject Name | Disaster Management |  Software Engineering |    C#    |   C++   | Java | ")
    print("CCE                   ",subjectOne[0],"                   ",subjectTwo[0],"              ",subjectThree[0],"      ",subjectFour[0],"    ",subjectFive[0])
    print("IAT                   ",subjectOne[1],"                   ",subjectTwo[1],"              ",subjectThree[1],"      ",subjectFour[1],"    ",subjectFive[1])
    print("TEE                   ",subjectOne[2],"                   ",subjectTwo[2],"              ",subjectThree[2],"      ",subjectFour[2],"    ",subjectFive[2])
    
    print("Total                ",gradeArray[0],actualGrade[0],"                ",gradeArray[1],actualGrade[1],"           ",gradeArray[2],actualGrade[2],"   ",gradeArray[3],actualGrade[3]," ",gradeArray[4],actualGrade[4])
}

var choice=0
while choice<4
{
    print("press\n1 to enter student details\n2.to enter enter marks\n3.to display the markscard\n4.to exit")
    choice=(Int)(readLine()!)!
    switch  choice
    {
    case 1:
        handleStudentInput()
    case 2:
        handleSubjectInput()
    case 3:
        gradeMethod()
        printMarksCard()
    case 4:
        print("Exit success")
    default:
        print("Invalid input")
    }
    
}




2.Shorting


Increasing order
var num = [8,3,5,4,6,7,3,2,1]
num.sort()
print(num)

Decreasing order
var num = [8,3,5,4,6,7,3,2,1]
num.sort(by: >)
print(num)



3.Switch Calculator


class rohaan
{
    func additonsum(num1:Int, num2:Int) ->Int
    {
        return num1+num2
    }
    
    func subraction(num3:Int, num4:Int) ->Int
    {
        return num3-num4
    }
    func multiplication(num5:Int,num6:Int)->Int
    {
        return num5-num6
    }
    func modules(num7:Int,num8:Int)->Int
    {
        return num7%num8
    }
    func divid(num9:Int,num10:Int)->Int
    {
        return num9/num10
    }
    
}

var obj = rohaan()

var switchvalue:Int = 1

switch(switchvalue)
{
case 1:print(obj.additonsum(num1: 10, num2: 20))

case 2:print(obj.subraction(num3:40, num4: 20))

case 3:print(obj.multiplication(num5:30, num6: 50))

case 4:print(obj.modules(num7:80, num8: 100))

case 5:print(obj.divid(num9:20, num10: 40))
    
default:print("cool")
}


4.Even odd


var myArray = [23, 54, 51, 98, 54, 23, 32];
        for myInt: Int in myArray{
            if myInt % 2 == 0 {
                print("\(myInt) is even number")
            } else if myInt % 2 != 0{
                print("\(myInt) is odd number")
            }
             
        }


5.Insertion Sorting


var numbers = [70, 36, 40, 95, 22, 55, 26]

print("We're going to sort these numbers: \(numbers)")

for index in 1..<numbers.count
{
    let value = numbers[index]
    var position = index

    print("- Inspecting value: \(value) at position: \(position)")

    while position > 0 && numbers[position - 1] > value
    {
        print("-- \(numbers[position-1]) > \(value), so shifting \(numbers[position-1]) to the right")

        numbers[position] = numbers[position - 1]
        position -= 1
 
        print("-> \(numbers)")
    }

    print("-- Found sorted position of \(value) is \(position), so inserting")

    numbers[position] = value

    print("-> \(numbers)")
    print("")
}

print(numbers)
