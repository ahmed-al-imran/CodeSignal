# CodeSignal

#reverseInParentheses

fun reverseInParentheses(inputString: String): String {
    var track      : Stack<Pair<Int, Int>> = Stack()
    var workString : String = inputString

	for(index in 0 until workString.length) {

		if(workString.get(index) == '(') track.push(Pair(index, -1))

		if(workString.get(index) == ')') {

			val pair : Pair<Int, Int> = Pair(track.peek().first, index)

			track.pop()

			workString = workString.substring(0, pair.first) + 
					workString.substring(pair.first, pair.second).reversed() +
					workString.substring(pair.second)
                    
		}

	}
    
    var returnString: String = ""
    
    for(index in 0 until workString.length)
        if(workString.get(index) != '(' && workString.get(index) != ')')
            returnString += workString.get(index)

	return returnString
}

============================================================

#Sort by Height

fun sortByHeight(a: MutableList<Int>): MutableList<Int> {
  var people: MutableList<Int> = mutableListOf()

	for(index in 0 until a.size)
		if(a[index] != -1) people.add(a[index])

    people.sort()

	var current : Int = 0

	for(index in 0 until a.size) {

		if(a[index] != -1) {

			a[index] = people[current]

			current++

		}

	}

	return a
}
  
====================================================
	
#commonCharacterCount

fun commonCharacterCount(s1: String, s2: String): Int {
  var shared : Int        = 0
	var hash1   = IntArray(26)
	var hash2   = IntArray(26)

	for(index in 0 until s1.length)
		hash1[s1[index] - 'a']++

	for(index in 0 until s2.length)
		hash2[s2[index] - 'a']++

	for(index in 0 until 26)
		shared += Math.min(hash1[index], hash2[index])


	return shared
}

