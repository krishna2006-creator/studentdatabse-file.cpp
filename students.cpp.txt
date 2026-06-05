/*
1. Add Student
2. View All Students
3. Search by RollNo
4. Delete by RollNo
5. Clear Database
6. Exit
*/
#include<unistd.h>
#include<iostream>
#include<vector>
#include<fstream>
using namespace std;
struct student{
string  rollno;
string name;
string  marks;
};
int main(){
vector<string>record;
vector<string>datas;
student s;
int choice=0;
do{
cout<<"\n 1.Add Student \n 2.View All Students \n 3.Search by RollNo \n 4.Delete by RollNo \n 5.Clear Database \n 6.add students at specific pos  \n 7.Exit"<<endl;
cout<<"enter your choice"<<endl;
cin>>choice;
if(choice==1){
cout<<"ADD STUDENTS DETAILS"<<endl;
int n;
cout<<"how many students to add in the database"<<endl;
cin>>n;
ofstream file("studentdata.txt",ios::app);
for(int i=0;i<n;i++){
cout<<"enter the rollno"<<":";
cin>>s.rollno;
cout<<"enter the name"<<":";
cin.ignore();
getline(cin,s.name);
cout<<"enter the marks"<<":";
cin>>s.marks;
file<<s.rollno<<"."<<s.name<<":"<<s.marks<<endl;
}
file.close();
}
else if(choice==2){
cout<<"view all students details"<<endl;
string line;
ifstream file("studentdata.txt");
while(getline(file,line)){
cout<<line<<endl;}
file.close();
}
else if(choice==3){
cout<<"enter the roll no to search"<<endl;
string  roll;
cin>>roll;
string line;
ifstream file("studentdata.txt");
while(getline(file,line)){
if(line.find(roll)!=string::npos){
cout<<line<<endl;
}
}
file.close();
}
else if(choice==4){
cout<<"delete by rollno"<<endl;
string roll;
string line;
ifstream file("studentdata.txt");
while(getline(file,line)){
datas.push_back(line);
}
file.close();
for(int i=0;i<datas.size();i++){
cout<<i+1<<":"<<datas[i]<<endl;
}
int pos=0;
cout<<"enter the roll no to delete"<<endl;
cin>>pos;
int n=pos-1;
datas.erase(datas.begin() + n);
//for(int i=0;i<datas.size();i++){
//if(i!=pos-1){
//record.push_back(datas[i]);

//}
ofstream fout("studentdata.txt",ios::trunc);
for(int i=0;i<datas.size();i++){
fout<<datas[i]<<endl;
}
fout.close();
}
else if(choice==5){
cout<<"clearing chat"<<endl;
for(int i=0;i<10;i++){
cout<<".";
cout.flush();
sleep(1);
}
cout<<"  loading";
cout<<"chat are cleared"<<endl;
ofstream file("studentdata.txt",ios::trunc);
file.close();
}/*
else if(choice==6){
cout<<"which postion u want to add"<<endl;
for(int i=0;i<datas.size();i++){
cout<<datas[i]<<endl;
}
int pos=0;
cout<<"enter the position to add"<<endl;
cin>>pos;
cout<<"enter the rollno"<<":";
cin>>s.rollno;
cout<<"enter the name"<<":";
cin.ignore();
getline(cin,s.name);
cout<<"enter the marks"<<":";
cin>>s.marks;
int l=pos-1;
string record=s.rollno+"."+s.name+":"+s.marks;
if(l>=0&&l<=datas.size()){
datas.insert(datas.begin()+l,record);
}
else{
cout<<"data is already is existed "<<endl;}
ofstream file("studentdata.txt",ios::trunc);
for(int i=0;i<datas.size();i++){
file<<datas[i]<<endl;
}
file.close();*/
}while(choice!=6);
return 0;
}


