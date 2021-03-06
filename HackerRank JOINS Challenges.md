
# Hackerrank_challenge

## The Report

Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students 
who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is
more than one student with the same grade (8-10) assigned to them,order those particular students by their name alphabetically. Finally, 
if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student 
with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.


### My solution:

`SELECT
    CASE WHEN Grades.Grade < 8 THEN NULL ELSE stu.Name END AS Name,
    Grades.Grade,
    stu.Marks
FROM
    Students stu INNER JOIN Grades ON stu.Marks BETWEEN Grades.Min_Mark and Grades.Max_Mark
ORDER BY
    Grades.Grade DESC,
    Name,
    stu.Marks`
    
    
    
    
## Top Competitors

Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective 
hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of 
challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by 
ascending hacker_id.



### My solution:
`select h.hacker_id, h.name from Submissions s join Hackers h 
on s.hacker_id = h.hacker_id 
join Challenges c on s.challenge_id = c.challenge_id
join Difficulty d on c.Difficulty_level = d.Difficulty_level
where s.score = d.score 
group by h.hacker_id, h.name 
having count(*) > 1
order by count(*) desc, h.hacker_id;`
