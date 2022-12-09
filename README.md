# 2022

### Day 1 #1

```bash
sed 's/^$/test/g' day1.input | xargs | sed 's/ /+/g' | sed 's/+test+/\n/g'  | while read line; do calc $line; done | sort -nr | head -1
```

### Day 1 #2

```bash
sed 's/^$/test/g' day1.input | xargs | sed 's/ /+/g' | sed 's/+test+/\n/g'  | while read line; do calc $line; done | sort -nr | head -3 | xargs | sed 's/ /+/g' | calc
```

### Day 2 #1

```bash
result=0; while read line; do if [[ $line == "B X" ]]; then result=$((result+1)); fi; if [[ $line == "C Y" ]]; then result=$((result+2)); fi; if [[ $line == "A Z" ]]; then result=$((result+3)); fi; if [[ $line == "A X" ]]; then result=$((result+4)); fi; if [[ $line == "B Y" ]]; then result=$((result+5)); fi; if [[ $line == "C Z" ]]; then result=$((result+6)); fi; if [[ $line == "C X" ]]; then result=$((result+7)); fi; if [[ $line == "A Y" ]]; then result=$((result+8)); fi; if [[ $line == "B Z" ]]; then result=$((result+9)); fi; done < day2.input; echo $result
```

### Day 2  #2

```bash
result=0; while read line; do if [[ $line == "A X" ]]; then result=$((result+3)); fi; if [[ $line == "A Y" ]]; then result=$((result+4)); fi; if [[ $line == "A Z" ]]; then result=$((result+8)); fi; if [[ $line == "B X" ]]; then result=$((result+1)); fi; if [[ $line == "B Y" ]]; then result=$((result+5)); fi; if [[ $line == "B Z" ]]; then result=$((result+9)); fi; if [[ $line == "C X" ]]; then result=$((result+2)); fi; if [[ $line == "C Y" ]]; then result=$((result+6)); fi; if [[ $line == "C Z" ]]; then result=$((result+7)); fi; done < day2.input; echo $result
```
### Day 3 #1

```bash
#!/bin/bash

split_string() {
  len=${#1}

  mid=$((len / 2))

  first=$(echo "$1" | cut -c -$mid)
  second=$(echo "$1" | cut -c $(($mid+1))-$len)
}

total_priority=0

while read line; do
  split_string "$line"

  common=$(tr -d -c "$second" <<< "$first" | fold -w1 | sort | uniq | tr -d '\n')

  for (( i=0; i<${#common}; i++ )); do
    char="${common:$i:1}"
    if [[ "$char" =~ [a-z] ]]; then
      total_priority=$((total_priority + 1 + $(printf "%d" "'$char") - $(printf "%d" "'a") ))
    elif [[ "$char" =~ [A-Z] ]]; then
      total_priority=$((total_priority + 27 + $(printf "%d" "'$char") - $(printf "%d" "'A") ))
    fi
   
  done
done <day3.input

echo "Total priority: $total_priority"
```

### Day 3 #2

```bash
#!/bin/bash

FILENAME="day3.input"

LINE_NUM=1

NUM_LINES=3

total_priority=0

while read line1; read line2; read line3; do
  char=$(tr -d -c "$line1" <<< "$line2" | tr -d -c "$line3" | fold -w1 | sort | uniq | tr -d '\n')

  if [[ "$char" =~ [a-z] ]]; then
      total_priority=$((total_priority + 1 + $(printf "%d" "'$char") - $(printf "%d" "'a") ))
  elif [[ "$char" =~ [A-Z] ]]; then
      total_priority=$((total_priority + 27 + $(printf "%d" "'$char") - $(printf "%d" "'A") ))
  fi

  total_priority=$((total_priority+priority))


  LINE_NUM=$((LINE_NUM+NUM_LINES))
done < "$FILENAME"

echo "Total priority: $total_priority"
```
