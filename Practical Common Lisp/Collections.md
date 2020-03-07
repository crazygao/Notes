---
title: Collections
tags: Others
grammar_cjkRuby: true
grammar_tableExtra: true
---
* Vectors
	* Create a vector
* Make Array
	* create 5 sized initial element vector
	* specify next poinsition to be filled
	* adjust the vector
	* push and pop
	* specify element type.
* Vector and Sequences
	* get length
	* get item place
	* count number of items
	* find item exist
	* find item position
	* remove item
	* replace with new item
	* count on string matches
	* find tuple with first key matches
	* limit start and end of find
	* find and position from end
* Higher Order Function Variants


%
* Vectors
	* (vector 1), #(1 2)
* Make-Array
	* (make-array 5 :initial-element nil)
	* (make-array 5 :initial-element 0 :fill-pointer 0)
	* (make-array 5 :adjustable t)
	* (vector-push val \*x\*) (vector-push-extend val \*x\*) (vector-pop val \*x\*)
	* (make-array 5 :adjustable t :element-type 'character)
* Vector and Sequences
	* (length \*x\*)
	* (elt \*x\* 2)
	* (count 1 #(1 2 1 2 3 1 2 3 4))         ==> 3
	* (find 1 #(1 2 1 2 3 1 2 3 4))          ==> 1
	* (position 1 #(1 2 1 2 3 1 2 3 4))      ==> 0
	* (remove #\a "foobarbaz")               ==> "foobrbz"
	* (substitute 10 1 #(1 2 1 2 3 1 2 3 4)) ==> #(10 2 10 2 3 10 2 3 4)
	* (count "foo" #("foo" "bar" "baz") :test #'string=)    ==> 1
	* (find 'c #((a 10) (b 20) (c 30) (d 40)) :key #'first) ==> (C 30)
	* (count "foo" #("foo" "bar" "baz") :test #'string= :start nil :end 2)    ==> 1
	* (find 'a #((a 10) (b 20) (a 30) (b 40)) :key #'first :from-end t) ==> (A 30)