- š Hi, Iām @khanhduy168
- š Iām interested in ...
- š± Iām currently learning ...
- šļø Iām looking to collaborate on ...
- š« How to reach me ...

<!---
khanhduy168/khanhduy168 is a āØ special āØ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->




#include<bits/stdc++.h>
using namespace std;
struct nhan_vien{
    int id;
    string name;
    int age;
    bool sex;
    string department;
    string sdt;
    string luong;
};
typedef nhan_vien NV;
void input(vector<NV> &ds){
    NV nv;
    bool check = true;
    do{
        system("cls");
        cout<<"Nhap id: ";cin>>nv.id;
        cin.ignore();
        int count = 0;
        if (ds.size() == 0)
            break;
        for (int i = 0; i < ds.size(); i++)
            if (ds[i].id == nv.id){
                count ++;
                break;
            }
        if (count == 0)
            check = false;
    }while (check);
    cout<<"Nhap ho ten nhan vien: ";getline(cin,nv.name);
    cout<<"Nhap tuoi: ";cin>>nv.age;
    int temp;
    cout<<"Gioi tinh (Nam: 1/Nu: 0): ";cin>>temp;
    if (temp == 1)
        nv.sex = true;
    else
        nv.sex = false;
    cin.ignore();
    cout<<"Nhap phong ban: ";getline(cin, nv.department);
    cout<<"Nhap sdt: ";cin>>nv.sdt;
    cout<<"Nhap luong: ";cin>>nv.luong;
    ds.push_back(nv);
}
void display(NV nv){
    cout<<nv.id<<"\t"<<nv.name<<"\t"<<nv.age<<"\t"<<((nv.sex) ? "Nam" : "Nu")<<"\t"<<nv.department<<"\t\t"<<nv.sdt<<"\t"<<nv.luong<<endl;
}
void pressAnyKey(){
    cout<<"\n\n";
    system("pause");
}
int main(){
	string user="cnpm12tlu";
	string pass="123456789a";
	
	string u;
	cout<<"Tai khoan:"<<endl;
	getline(cin,u);
	string p;
	cout<<"Mat khau: "<<endl;
	getline(cin,p);
	while(user !=u || pass!=p )
	{
		cout<<"Tai khoan hoac mat khau khong chinh sac. Vui long thu lai " <<endl;
		
		cout<<"Tai khoan:"<<endl;
		getline(cin,u);
		cout<<"Mat khau: "<<endl;
		getline(cin,p);
	}
	cout<<"Dang nhap thanh cong "<<endl;
    vector<NV> ds;
    int key;
    while (true){
        system("cls");
        cout<<"Don vi quan ly: Bui Pham Khanh Duy\t\tChuc vu: Truong phong hanh chinh nhan su\n";
        cout<<"1. Them nhan vien .                               \n";
        cout<<"2. Xoa nhan vien bang ID.                          \n";
        cout<<"3. Tim kiem nhan vien theo ID.                    \n";
        cout<<"4. Hien thi nhan vien theo luong giam dan.        \n";
        cout<<"5. Hien thi danh sach nhan vien.                  \n";
        cout<<"0. Thoat                                          \n";
        cout<<"Nhap tuy chon: ";
        cin>>key;
        int idrm;
        switch (key){
            case 1:
                system("cls");
                input(ds);
                pressAnyKey();
                break;
            case 2:
                system("cls");
                cout<<"Nhap ID nhan vien can xoa: ";cin>>idrm;
                for (int i = 0; i < ds.size(); i++){
                    if (ds[i].id == idrm){
                        char c;
                        cout<<"Ban co chac muon xoa!!! (Y/N) ";cin>>c;
                        if (c == 'Y' || c =='y')
                            ds.erase(ds.begin() + i);
                        break;
                    }
                }
                pressAnyKey();
                break;
            case 3:
                system("cls");
                cout<<"Nhap ID can tim kiem: ";cin>>idrm;
                system("cls");
                cout<<"ID\t\t  Ho Ten\tTuoi\tGTinh\tPhong ban\t\tSDT\t\tLuong\n";
                for (int i = 0; i < ds.size(); i++){
                    if (ds[i].id == idrm){
                        display(ds[i]);
                        break;
                    }
                }
                pressAnyKey();
                break;
            case 4:
                {system("cls");
                vector<NV> temp = ds;
                for (int i = 0; i < temp.size(); i++)
                    for (int j = 0; j <= i; j++)
                        if (temp[i].luong > temp[j].luong)
                            swap(temp[i], temp[j]);
                cout<<"Danh sach nhan vien:\n";
                cout<<"ID\t\t  Ho Ten\tTuoi\tGTinh\tPhong ban\t\tSDT\t\tLuong\n";
                for (int i = 0; i < temp.size(); i++)
                    display(temp[i]);
                pressAnyKey();
                break;}
            case 5:
                system("cls");
                cout<<"Danh sach nhan vien:\n";
                cout<<"ID\t\t  Ho Ten\tTuoi\tGTinh\tPhong ban\t\tSDT\t\tLuong\n";
                for (int i = 0; i < ds.size(); i++)
                    display(ds[i]);
                pressAnyKey();
                break;
            case 0:
                return 0;
            default:
                system("cls");
                cout<<"Khong co chuc nang nay!\n";
                cout<<"Hay chon chuc nang trong menu.";
                pressAnyKey();
                break;
        }
    }
}
