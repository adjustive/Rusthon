String
------
the c++ backend translates strings into `std::string`.

```rusthon

myglobal = 'hi'
def main():
	u = 'X'
	print len(u)

	a = 'XYZ'
	print( a[0] == 'X' )
	print( a[-1] == 'Z' )
	print myglobal[-1]

	print( a[0:2] == 'XY' )
	print a[0:2]
	print a[:2] == 'XY'

	print a[1:3] == 'YZ'
	print a[1:] == 'YZ'

	#print a.lower()  ## TODO
	#print a.upper()

	print ord('A')  ## should be 65
	print chr(65)   ## should be 'A'

	v1 = a.split()
	print v1
	print len(v1)
	print v1[0]

	abc = 'a b c'
	print abc
	v2 = abc.split()
	print v2
	print len(v2)

	print 'ok'

```