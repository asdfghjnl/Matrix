/*
# Matrix
Just another respository

*/


#include "Base.h" 

typedef struct{
    int row;
    int cols;
    int** data;
}Matrix;

//helper function,  creater function 
//int,  int  -> Matrix*
Matrix* new_matrix(int cols, int row){
    return xcalloc(1, sizeof(Matrix*));
}

//helper function,  copy function 
//int*, int,  int -> Matrix*
Matrix* copy_matrix(int* data, int cols, int row){
    Matrix* m = new_matrix(cols, row);
    for(int i = 0; i < (m->cols * m->row); i++){
        *(m->data[i]) = data[i];
    }
    return m;
}

//helper function, accessor function 
//Matrix* -> int
int accessor_row(Matrix* m);

//helper function, accessor function 
//Matrix* -> int
int accessor_cols(Matrix* m);

//helper function, accessor function 
//Matrix* -> int**
int** accessor_data(Matrix* m);

//helper function, print function 
//Matrix* -> void
void print_matrix(Matrix* m){
    for(int i = 0; i < (m->cols * m->row); i++){
        if(( (i+1) % m->row) == 0) printf("\n");
        printf("%d ", m->data[i]);
    }
}

void Test_matrix(void){
    Matrix* m0 = new_matrix(7,1);
    print_matrix(m0);
    free(m0);
    int a[] = {
        1, 2 , 3,
        4, 5, 6,
        7, 8, 9};
    matrix* m1 =copy_matrix(a, 3, 3);
    print_matrix(m1);
    free(m1);
}

int main(void){
    Base_init();
    Base_set_memory_check(true);
    test_matrix();
    return 0;
}

