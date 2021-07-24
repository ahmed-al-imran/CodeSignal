# CodeSignal

#reverseInParentheses

fun reverseInParentheses(inputString: String): String {
    var track      : Stack<Pair<Int, Int>> = Stack()
    var workString : String                = inputString

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
