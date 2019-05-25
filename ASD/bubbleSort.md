void bubbleSort(string& A)
{
    for(size_t i = 1;i < A.size()-1;i++){
       for(size_t j = 1;j < i-1;j ++){
          if(A.at(j) > A.at(j+1)){
             swap(A.at(j),A.at(j+1));
          }
          cout << A << endl;
       }
    }
    
}