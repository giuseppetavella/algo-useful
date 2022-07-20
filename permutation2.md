```python
# permutation algorithm giving you full control over permutation process
# you can edit or ignore values and lists in permutation process
# it is complete, beautifully readable, efficient, customizable, giving you control in every step

# to optimize- use arrays instead of lists?
# to optimize- give option for only uniques


def permute_all(to_permute, fn_val, fn_checkval, fn_list, fn_checklist):
    size_to_permute = len(to_permute)
    perms = [[]]
    def perm(i_row, row, prev_p_list):
        # last row
         if i_row+1 == size_to_permute:           
            for p in row:
                if fn_checkval(p): 
                    continue
                # final step for one permutation
                lst = prev_p_list+[fn_val(p)]
                if fn_checklist(lst):
                    continue
                perms[-1].append(fn_list(lst))
            perms.append([])
            return   
        # all other rows
         for p in row:
            if fn_checkval(p): 
                continue
            perm(i_row+1, to_permute[i_row+1], prev_p_list+[fn_val(p)])
    perm(0, to_permute[0], [])
    perms.pop()
    return perms
             

    
# gets invoked before performing any operation
# output True means that this value will NOT be included in the permutation
# this value will be skipped
# output boolean
def perm_checkval(p):
    return p == None
    
    
# this list will be skipped 
def perm_checklist(p_list):
    return False

    
    
# gets invoked for every value that 
def perm_editval(p):
    return p

    

# what to do with each permutation
# gets invoked on the whole list after permutation is done and you want to edit outcome
# input list, output list
def perm_editlist(p_list):
    return ''.join(p_list)
    # if you want all permutated values in list, use:
#     return p_list

    
    

list_to_permute = [
    ['a', 'b', 'c'],
    ['d', 'e', 'f'],
    ['g', 'h', 'i']
]   

    
    
permutations_all = permute_all(to_permute=list_to_permute, 
                               fn_list=perm_editlist, 
                               fn_val=perm_editval, 
                               fn_checkval=perm_checkval, 
                               fn_checklist=perm_checklist)

permutations_all
# np.unique(permutations_all)
```




    [['adg', 'adh', 'adi'],
     ['aeg', 'aeh', 'aei'],
     ['afg', 'afh', 'afi'],
     ['bdg', 'bdh', 'bdi'],
     ['beg', 'beh', 'bei'],
     ['bfg', 'bfh', 'bfi'],
     ['cdg', 'cdh', 'cdi'],
     ['ceg', 'ceh', 'cei'],
     ['cfg', 'cfh', 'cfi']]




```python

```
