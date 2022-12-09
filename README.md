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
