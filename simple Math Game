#include <iostream>
#include<cstdlib>
#include<ctime>
using namespace std;

enum enLevel { Easy = 1, Mid, Hard, Mix };
enum enOperator { Add = 1, Sub, Mul, Div, MIX };

struct stQuiseQustion
{
    int Number1 = 0;
    int Number2 = 0;
    enOperator Operator;
    enLevel level;
	int CorrectAnswer = 0;  
	int PlayerAnswer = 0;   
    bool AnswerRuselt = false;

};

struct  stQuizeResult
{
    stQuiseQustion Qustion[100];
    short NumberOfQustion = 0;
    short NumberOfRigtAnswer = 0;
    short NumberOfWrongAnswer = 0;
    enLevel  QuestionsLevel;
    enOperator OpType;
    string opretorName = " ";
    string ExamResult = "";
    string LevelName = "";
	bool IsPass = false;    
};

int RandomNumber(int From, int To)
{
    int Random = rand() % (To - From + 1) + From;
    return Random;
}

int  AskUser(string Massege)
{
    int Ques = 0;
    do
    {
        cout << Massege;
        cin >> Ques;
    } while (Ques < 1 || Ques>10);
    return Ques;
}

enLevel QuestionLevel()
{
    short QuesLevel = 0;
    do
    {
        cout << "Enter Question Level , [1] Easy , [2] Mid , [3] Hard , [4] Mix ? \n";
        cin >> QuesLevel;
    } while (QuesLevel < 1 || QuesLevel>4);

    return enLevel(QuesLevel);
}

enOperator OperationType()
{
    short ope = 0;
    do
    {
        cout << "Enter Operation Type : [1] Add , [2] Sub , [3] Mul , [4] Div ,[5] Mix \n ";
        cin >> ope;
	} while (ope < 1 || ope>5); 

    return enOperator(ope);
}

void Color( bool IsAnswer)
{
    if (IsAnswer)
        system("color 2F");
    else
    {
        cout << "\a";
        system("color 4F");
    }
}

void CorrectTheQustionAnswer( stQuizeResult &Quizzz, short QustionNumber)
{
    if (Quizzz.Qustion[QustionNumber].PlayerAnswer !=Quizzz.Qustion[QustionNumber].CorrectAnswer)
    {
		cout << "\n\n Wrong Answer :( , The Correct Answer is  : " << Quizzz.Qustion[QustionNumber].CorrectAnswer;  
        Quizzz.Qustion[QustionNumber].AnswerRuselt = false;
        Quizzz.NumberOfWrongAnswer++;
       
    }
    else
    {
        cout << "\n\n Right Answer :)  " << endl;
        Quizzz.Qustion[QustionNumber].AnswerRuselt = true;
        Quizzz.NumberOfRigtAnswer++;
    }
    Color(Quizzz.Qustion[QustionNumber].AnswerRuselt);
}

string GetLevelName(enLevel Level)
{
    string arr[4] = { "Easy" , "Mid","Hard","Mix" };

    return arr[Level - 1];
}

char opchar(enOperator ope)
{
    char  arr[5] = { '+','-','*','/',' ' };

    return arr[ope - 1];

}

string GetOpeType(enOperator ope)
{
    string arr[5] = { "Add", "Sub", "Mil", "Div", "Mix" };

    return arr[ope - 1];
}

string  Tabs(short num)
{
    string t = "";
    for (int i = 0;i < num; i++)
    {
        t += "\t";
    }
    return t;
}

void SetExamResult(stQuizeResult& QuizeResult)
{

    if (QuizeResult.NumberOfRigtAnswer >= QuizeResult.NumberOfWrongAnswer)
    {
        QuizeResult.ExamResult = "Pass";
    }
    else
    {
        QuizeResult.ExamResult = "Fail";
    }
}

void PrintRoundRuselt(stQuizeResult& QuizeResult, int QuestionNumber)
{

    cout << "\n\n Round [ " << QuestionNumber + 1 << " / " << QuizeResult.NumberOfQustion << " ] \n " << endl;
    cout << QuizeResult.Qustion[QuestionNumber].Number1 << endl;
    cout << QuizeResult.Qustion[QuestionNumber].Number2 << " ";
	cout << opchar(QuizeResult.Qustion[QuestionNumber].Operator) ;
    cout << "\n\n--------------------------------\n";

}

int  simpleCalculater(int Number1, int Number2, enOperator op)
{

    switch (op)
    {
    case enOperator::Add:
        return Number1 + Number2;
    case enOperator::Sub:
        return Number1 - Number2;
    case enOperator::Mul:
        return Number1 * Number2;
    case enOperator::Div:
        return Number1 / Number2;
    }
    return Number1 + Number2;
}

enOperator  MixOpretor()
{
    return enOperator(RandomNumber(1, 4));
}

int ReadQustionsAnswer()
{
    cout << "\n";
    int Answer = 0;
    cin >> Answer;
    return Answer;
}

stQuiseQustion  GenerateQuiseQustion( enLevel Level,enOperator op )
{
	stQuiseQustion Qustion; 

    if (  Level == enLevel::Mix )
    {
		Level = enLevel(RandomNumber(1, 3));    
     }
    if (op == enOperator::MIX)
    {
       op = MixOpretor();
    }
    switch (Level)
    {

    case enLevel::Easy:

       Qustion.Number1  = RandomNumber(1, 10);
       Qustion.Number2 = RandomNumber(1, 10);
	     
       break;
     
    case enLevel::Mid:

        Qustion.Number1 = RandomNumber(10, 50);
        Qustion.Number2 = RandomNumber(10, 50);
     
        break;

    case enLevel::Hard:
        Qustion.Number1 = RandomNumber(50, 100);
        Qustion.Number2 = RandomNumber(50, 100);
       
        break;
    }
    Qustion.CorrectAnswer = simpleCalculater(Qustion.Number1, Qustion.Number2, op);
	Qustion.Operator = op;  
    Qustion.level = Level;
    return Qustion;
}

void  GenerateQuiseQustions(stQuizeResult& QuizeResult)
{
    for (int i = 0;i<QuizeResult.NumberOfQustion;i++)
    { 

      QuizeResult.Qustion[i] = GenerateQuiseQustion(QuizeResult.QuestionsLevel,QuizeResult.OpType);
       
    }
	QuizeResult.opretorName = GetOpeType(QuizeResult.OpType);   
	QuizeResult.LevelName = GetLevelName(QuizeResult.QuestionsLevel);   
}

void AskAndCorrectQustionsListAnswer(stQuizeResult& QuizeResult)
{
    for (int QuestionNumber = 0; QuestionNumber < QuizeResult.NumberOfQustion;QuestionNumber++)
    {
        PrintRoundRuselt(QuizeResult, QuestionNumber);
		QuizeResult.Qustion[QuestionNumber].PlayerAnswer = ReadQustionsAnswer();    
        CorrectTheQustionAnswer(QuizeResult, QuestionNumber);   

    }

	QuizeResult.IsPass = (QuizeResult.NumberOfRigtAnswer >= QuizeResult.NumberOfWrongAnswer);
 }

void PrintGameResult(stQuizeResult QuizeResult)
{
    cout << "\n_____________________________________________\n";
    cout << Tabs(2) << "--- G A M E   R E S U L T S --- \n";
    cout << "_____________________________________________\n";
    cout << Tabs(2) << "\n\n Round Times :  " << QuizeResult.NumberOfQustion;
	cout << Tabs(2) << "\n\n Game Result :  " << (QuizeResult.IsPass ? "Pass" : "Fail");    
    cout << Tabs(2) << "\n Opretor Use : " << QuizeResult.opretorName;
    cout << Tabs(2) << " \nGame Level : " << QuizeResult.LevelName;
    cout << Tabs(2) << " \nNumber Of Right Answer : " << QuizeResult.NumberOfRigtAnswer;
    cout << Tabs(2) << " \nNumber Of Wrong Answer : " << QuizeResult.NumberOfWrongAnswer;
    cout << "\n_____________________________________________\n";
}

void PlayGame()
{
    stQuizeResult QuizeResult;

    QuizeResult.NumberOfQustion = AskUser(" How Many Questions do you want to Answer \n ");
    QuizeResult.QuestionsLevel = QuestionLevel();
    QuizeResult.OpType = OperationType();

        GenerateQuiseQustions(QuizeResult);

		AskAndCorrectQustionsListAnswer(QuizeResult);

        PrintGameResult(QuizeResult);
    
       
}

void ResetScreen()
{
    system("cls");
    system("color 0F");
}

void StartGame()
{
    char PlayAgain = 'Y';
    do
    {
        ResetScreen();
        PlayGame();

        cout << Tabs(2) << "\n Do You Wint To Play Again  ? \n";
        cin >> PlayAgain;
    } while (PlayAgain == 'Y' || PlayAgain == 'y');

}

int main()
{
    srand((unsigned)time(NULL));

    StartGame();
    return 0;
}
