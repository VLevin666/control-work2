#include <iostream>
#include "math.h"

using namespace std;

template <typename T>
class koren {
private:
	T x;
	T korenx;

public:
	koren(T x) {
		this->x = x;
		korenx = sqrt(x);
	}

	T getkoren() { 
		return korenx;
	}

	void setx(T x) { 
		this->x = x;
		korenx = sqrt(x);
	}

	void setkorenx(T korenx) {
		this->korenx = korenx;
		x = korenx * korenx;
	}

	koren operator * (koren<T> dis) {
		koren<T> res(x);
		res.setkorenx(korenx * dis.korenx);
		return res;
	}

	koren operator / (koren<T> dis) {
		koren<T> res(x);
		if (dis.korenx != 0) {
			res.setkorenx(korenx / dis.korenx);
			return res;
		}
		else return -1;
	}
};

int main()
{
	double a, b;
	cout << "Enter 2 numbers:" << endl;
	cout << "Enter first number: ";
	cin >> a;
	cout << "Enter second number: ";
	cin >> b;
	cout << endl;
	cout << "Result:" << endl;

	koren<double> k1(a);
	koren<double> k2(b);
	koren<double> u(0);
	koren<double> d(0);
	u = k1 * k2;
	d = k1 / k2;

	cout << "sqrt(" << a << ")" << "*" << "sqrt(" << b << ")" << "=" << u.getkoren() << endl;
	cout << "sqrt(" << a << ")" << ":" << "sqrt(" << b << ")" << "=" << d.getkoren() << endl;

	return 0;
}
