#include<iostream>
using namespace std;
class DynamicArray {
private:
	int size;
	int *array;
	
public:
	DynamicArray( )
	{
		size = 0;
		array = nullptr;
	}
	DynamicArray( int* arr, int size )
	{
		this->size = size;
		array = new int[size];
		for ( int i = 0; i < size; i++ )
		{
			array[i] = arr[i];
		}

	}
	void add( int element )
	{
		int *NewArray = new int[size+1];
		for ( int i = 0; i < size; i++ )
		{
			NewArray[i] = array[i];
		}
		NewArray[size] = element;
		delete[] array;
		array = NewArray;
		size++;
	}
	bool removeAt( int index )
	{
		if ( index<0 || index>size )
		{
			return false;
		}
		else
		{
			for ( int i = 0; i < size-1; i++ )
			{
				if ( i == index||i>index )
				{
					array[i] = array[i + 1];
				}
			}
			size--;
			return true;
		}
	}
	int get( int index ) const
	{
		return array[index];
	}
	int Size( ) const
	{
		int count = 0;
		for ( int i = 0; i < size; i++ )
		{
			count += 1;
		}
		return count;
	}
	
	int search( int element,int size )
	{
		if ( size < 0 )
		{
			cout << "Not found!";
			return -1;
		}
		else
		{
			if ( array[size] == element )
			{
				cout << "Found!";
				return array[size];
			}
			else
			{
				search( element, size - 1 );
			}
		}
		
	}
	void sort( )
	{
		for ( int i = 0; i < size - 1; ++i ) {
			for ( int j = 0; j < size - i - 1; ++j ) {
				if ( array[j] > array[j + 1] ) {
					int temp = array[j];
					array[j] = array[j + 1];
					array[j + 1] = temp;
				}
			}
		}
	}
	void Display( )
	{
		cout << "size: " << size << endl;
		cout << "Array elements: ";
		for ( int i = 0; i < size; i++ ) {
			cout << array[i] << " "; 
		}
		cout << endl;
	}
	 ~DynamicArray( )
	 {
		 delete[] array;
	 }
};
int main( )
{
	int size, op; bool decision=true;
	int number; int rem;
	cout << "Enter the number of elements: " << endl;
	cin >> size;
	int* array = new int[size];
	cout << "Enter element in the array: " << endl;
	for ( int i = 0; i < size; i++ )
	{
		cin >> array[i];
	}
	DynamicArray arr1(array,size );
	arr1.Display( );
	cout << "-------------------------------------" << endl;
	cout << "1.Add the element to an array." << endl;
	cout << "2.Remove the element on the specific index." << endl;
	cout << "3.Access the element from given index." << endl;
	cout << "4.Current size of the array." << endl;
	cout << "5.Search an element from an array." << endl;
	cout << "6.Sort the element of an array." << endl;
	cout << "7.you want to exit." << endl;
	while ( 1 )
	{
		cout << "Enter number of operation you want to perform on array:" << endl;
		cin >> op;
		switch ( op )
		{
		case 1:
		{
			cout << "Enter number you want to add to the array: " << endl;
			cin >> number;
			arr1.add( number );
			arr1.Display( );
			break;
		}
		case 2:
		{
			
			cout << "Remove the number of element at index: " << endl;
			cin >> rem;
			arr1.removeAt( rem );
			arr1.Display( );
			break;
		}
		case 3:
		{
			cout << "Enter the index of element you want to get: " << endl;
			cin >> rem;
			cout << "The number is: " << arr1.get( rem ) << endl;
			break;
		}
		case 4:
		{
			cout << "Current size of array: " << endl;
			cout << arr1.Size( );
			break;
		}
		case 5:
		{
			cout << "Enter element in the array you want to search: " << endl;
			cin >> rem;
			cout << arr1.search( rem, size ) << endl;;
			break;
		}
		case 6:
		{
			arr1.sort( );
			arr1.Display( );
			break;
		}
		default:
		{
			cout << "Do you want to continue operation(true or false)?" << endl;
			cin >> decision;
			if ( decision == false )
			{
				exit( 1 );
			}
		}
		}
	}
	delete[] array;

}

