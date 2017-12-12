# SuperUsefull


# 1. Touch all files
find  -type f  -name "*" -exec touch {} +

# 2. nb of elements within folder
find . -type d -print0 | while read -d '' -r dir; do
    files=("$dir"/*)
    printf "%5d files in directory %s\n" "${#files[@]}" "$dir"
done

# 3.  Recursive grep
 find . -type f -exec grep -l "VC0860_VC0860_Hypothetical" {} +
