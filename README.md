# numpy-note
# Basic

  **1.to import:**
  
    import numpy as np
    ->can use int,float..any type value
  **2. One dimensional array:**
  
    a = np.array([1,2,3])
  
**3. Two dimensional array:**

	b = np.array([[2.9,4.3,4.6],[6.0,8.6,7.6]])
**4. To get dimension of the array:**

	b.ndim
**5. To get type of the array:**

	b.dtype
**6. To get Shape:**
	b.shape 
	->gave (2,3) means 2 row 3 column
**7. to set data type explicitly(automatically the will give us int32):**

	c = np.array([1,2,3],dtype='int32')
	->that means it will take size 32 bit or 4 byte
**8. to get size(how much space it takes) of an array:**

	c.itemsize
**9. to get length(how many item it has) :**

	c.size
	->[1,5,4,3]=4 value=4 size
**10. to get specific element from an array:**

	b[1,2]
	->b[row,column] (we can use negative number too like list)
**11. to get a specific range row:**

	b[0,:]
**12. to get aspecific range column:**

	b[:,1] 
**13. to get more specific:**

	b[1,1:]
	->[row,startindex(of column): ]
**14. to get more specific version 2:**

	b[0,1:6:2]
	->[row,startindex(of column):endindex(of column):step(of column)] {endindex is not included}
**15. to change a value of the array:**

	d[1,2] = 12.6
**16. to change a bunch of value of an array at the same time with same value:**

	d[1,1:4]=5
	->d[row,startindex:endindex] = 5
	-> means all value of startindex to endindex will be 5.
**17. to change a bunch of value of an array at the same time with different value:**

	d[1,1:4]=[5,8,4]

# 3D array:

**18. to create 3d array:**

	e=np.array([[[1,2,3],[4,5,6]],
		    [[9,8,7],[6,1,3]]])
**19. to get value from 3d array:**

	e[0,1,1]
	->0 = first row of the array.([[1,2,3],[4,5,6]])
**20. to get a specific range row from 3d array:**

	e[0,1,0:]
**21. to get a specific range column from 3d array:**

	e[0:,1,0]
**22. to replace value from a 3d array:**

	e[:,1,0]=[5,8]

# initialize:

**23. All zeros matrix:**

	f=np.zeros([2,3])
	->2 row,3 column
**24. All ones matrix:**

	f=np.ones([2,3], dtype='int32')
	->can explicitly set data type
**25. any other number matrix:**

	g=np.full([2,2],99)
	->all row and column value will be 99.
**26. full_like:**

	h=np.full_like(a,3)
	-if we have an array call a ,,then we can use 'a' array's shape to create all 3 value's array.
	
**27. to create a random array:**

	i=np.random.rand(2,3)
**28. to create an array shape from previous any array:**

	j=np.random.random_sample(a.shape)
**29. to create an integare base random array:**

	np.random.randint(2,8,size=(2,3))
	->2,8=random number
**30. to create idwntity matrix:**

	np.identity(4)
**31. repeat an array on y axis:**

	arr = np.array([[1, 2, 3]])
	r1 = np.repeat(arr,4,axis=0)
**32. repeat an array on x axis:**

	arr = np.array([[1, 2, 3]])
	r1 = np.repeat(arr,4,axis=1)


# copying array:

**33. Copying array:**

	a=np.array([1,2,3])
	b=a.copy()

# Mathmatics:

**34. Can do any math operation with array:**

	a=np.array([1,2,3])
	a+=2
	a-=2
	a*=2
	a=a/2
	a=a**3
	b=np.array([4,5,6])
	c=a+b
**35. can do trigonomatric operation:**

	np.cos(a)
	->like that can do sic=n,tan,cot

# Linear Algebra:

**36. Matrix addition:**

	a=np.array([[1,2,3],[4,5,6]])
	b=np.array([[8,8],[7,7],[9,9]])

	np.matmul(a,b)
**37. To find the determinant:**

	a=np.identity(3)
	print(np.linalg.det(a))

# Statics:

**38. to find min,max,sum:**

	stats=np.array([[1,2,3],[4,5,6]])
	np.max(stats,axis=1)
	->axis=1 means check on rows individually,axis=0 means check on column individually

	np.min(stats)
	np.sum(stats)

# Reorganizing arrays:

**39. reshape an array shape:**

	a=np.array([[1,2,3],[4,5,6]])
	b=a.reshape([3,2])
	->We can reshape 'a' array. But have to maintain shape with value's of a.
**40.Vertically stacking vectors:**

	v1=np.array([1,2,3,4])
	v2=np.array([5,6,7,8])

	v3=np.vstack([v1,v2,v2,v1])
**41.Horizontal stack:**

	h1=np.array([1,2,3,4])
	h2=np.array([5,6,7,8])

	h3=np.hstack([v1,v2,v2,v1])
  
# Load data from file:

**42. load data from a file:**

	filedata=np.genfromtxt('data.txt', delimiter=',')
	filedata=filedata.astype('int16')
	print(filedata)
	->delimiter = to seperate every value from data.txt file.
	->automatically filedata gives us float value. but we want 
	->int value that's why we turn float value to int value.
  
# Boolean masking and indexing:

**43. condition:**

	print(filedata>30)
	->if filedata's value is greater than 30 it will print true else false.
**44. condition which gives value**

	print(filedata[filedata>50])
	->if filedata's value is greater than 50 it will print that value else it won't.
**45. Check from whole file:**

	np.any(filedata>5090)
	->if any of the value from filedata is greater than 5090 it will give us true
	->else false
**46. check on column base:**

	np.any(filedata>50, axis=0) 
	->it will check every column,,if any column's any value is greater than
	->50 it will give us true otherwise false.
	->when x=1 it will check on row base.
	->if we use np.all instead of np.any it will gives us true only if 
	->column's or row's all value's are greater than 50.
**47. More condition:**

	~((filedata>50) & (filedata<700))
	->&=and,~=not
**48. We can indexing for list:**

	a=np.array([1,2,3,4,5,6,7,8,9])
	print(a[[1,2,6]])



