# IPL-Sports-Analysis-Project
IPL  Sports Analysis Project Using PostgreSQL.
!alt text: ![Image](https://github.com/user-attachments/assets/fe4b1d4c-e259-4f15-ab39-028cae84886e)


# (1). Find Player Whose SR is Above 120.

SELECT Player, Runs, BF, Against, Venue, Match_Date
FROM Fatest_Centuries
WHERE Runs >= '120'
ORDER BY Runs DESC;
Link Text :[data-3.csv](https://github.com/user-attachments/files/19721811/data-3.csv)


# (2). To Get The Player Hit Maximum Ton Against Each IPL Franchies.

SELECT COUNT(Player) AS Total_Player, Against
FROM Fatest_Centuries
GROUP BY Against
ORDER BY Total_Player DESC;
Link Text: [data- 2.csv](https://github.com/user-attachments/files/19721827/data-.2.csv)


# (3). Highest Runs In An Innings By Individual Player, With Their States.

SELECT *
FROM Fatest_Centuries
WHERE Runs = (SELECT MAX(Runs) FROM Fatest_Centuries);
Link Text : [data-3.csv](https://github.com/user-attachments/files/19721832/data-3.csv)


# (4). Highest Dots Balls Per Innings By Individual Player, With Their States.
SELECT *
FROM Most_Dot_Balls_Inning
WHERE Dots = (SELECT MAX(Dots) FROM  Most_Dot_Balls_Inning);
Link Text : [data-4.csv](https://github.com/user-attachments/files/19721855/data-4.csv)


# (5). Named Player Who Become Highest Wicket Taker and Most Dot Ball Per Inning Against Each IPL Franchies.

SELECT  Most_Dot_Balls_Inning.Player
, Most_Dot_Balls_Inning.Dots
, Most_Wicket.Wkts
, Most_Wicket.bbi
, Most_Dot_Balls_Inning.Against
, Most_Dot_Balls_Inning.Match_Date
FROM Most_Wicket
INNER JOIN Most_Dot_Balls_Inning
ON Most_Wicket.Player = Most_Dot_Balls_Inning.Player
WHERE Most_Dot_Balls_Inning.Against = (SELECT MAX(Most_Dot_Balls_Inning.Against) FROM Most_Dot_Balls_Inning)
ORDER BY Most_Wicket.Wkts DESC;
Link Text : [data-5.csv](https://github.com/user-attachments/files/19721859/data-5.csv)


# (6). Find Out Top 5 Player Who Hit Most Sixes in a IPL Season. 

SELECT User_Id
, Player
, Mat
, Inns
, Runs
, HS
, SR
, Hundred
, fifties
, Fours
, Sixes
FROM Most_Runs
WHERE Sixes >= '30'
ORDER BY Sixes DESC
LIMIT 5;
Link Text :[data- 6.csv](https://github.com/user-attachments/files/19721868/data-.6.csv)


# (7). In IPL History Pick Top Player who Ton Above 150.

SELECT * 
FROM Fatest_Centuries
WHERE Runs >= '150';
Link Text :[data- 7.csv](https://github.com/user-attachments/files/19721873/data-.7.csv)


# (8). --Pick Top Player Who Score A Ton Against IPL Team 'CSK'.

SELECT Player, Runs, BF, Against, Venue, Match_Date
FROM Fatest_Centuries
WHERE Against = 'CSK'
ORDER BY Runs DESC;
Link Text :[data- 8.csv](https://github.com/user-attachments/files/19721878/data-.8.csv)


# (9). To Get List of Player Who Score Equal & Less Than 25 And Run Score Greater Than & Equal to 60. 

SELECT Player
, Runs
, BF
, Against
, Venue
, Match_Date
FROM Fatest_Fifties
WHERE BF <= '25' AND Runs >= '60'
ORDER BY BF ASC;
Link Text :[data- 9.csv](https://github.com/user-attachments/files/19721883/data-.9.csv)


# (10). Find Out Maximum Times Player Hit Fatest Fifties against Each IPL Franchies. 

SELECT COUNT(Player) AS Total_Player
, Against
FROM Fatest_Fifties
WHERE BF <= '25' AND Runs >= '60'
GROUP BY Against
ORDER BY Total_Player DESC;
Link Text :[data- 10.csv](https://github.com/user-attachments/files/19721890/data-.10.csv)


# (11). Maximum Number of time A Player Hit Fatest Fifties Against IPL Franchies.

SELECT MAX(Player) AS Total_Player
, Against
FROM Fatest_Fifties
GROUP BY Against
ORDER BY Total_Player DESC;

Link Text : [data- 11.csv](https://github.com/user-attachments/files/19721895/data-.11.csv)


# (12). Find Player WhO Score At Least Fifties and Centuries Against IPL Franchies. 

SELECT Fatest_fifties.Player AS Players
, Fatest_fifties.Runs AS Fifties_Runs
, Fatest_fifties.BF
, Fatest_Centuries.Runs AS Centuries_Runs
, Fatest_Centuries.BF
, Fatest_Centuries.Against
, Fatest_Fifties.Venue
, Fatest_Centuries.Match_Date
FROM Fatest_Centuries
INNER JOIN Fatest_fifties
ON Fatest_Centuries.Player = Fatest_fifties.Player
WHERE Fatest_fifties.Runs >= '80' AND Fatest_Centuries.Runs >= '130'
ORDER BY Players ASC;

Link Text :[data- 12.csv](https://github.com/user-attachments/files/19721921/data-.12.csv)

# (13). Pick Top 5 Player Who Hit's Fatest Centuries and Fifties Against, Venue With Match_Date.

SELECT Fatest_fifties.Player
, Fatest_fifties.Runs
, Fatest_fifties.BF
, Fatest_Centuries.Runs
, Fatest_Centuries.BF
, Fatest_Centuries.Against
, Fatest_Fifties.Venue
, Fatest_Centuries.Match_Date
FROM Fatest_Centuries
INNER JOIN Fatest_fifties
ON Fatest_Centuries.Player = Fatest_fifties.Player
WHERE Fatest_fifties.BF = '35' OR Fatest_Centuries.BF = '35'
ORDER BY  Fatest_Centuries.BF ASC, Fatest_fifties.BF ASC
LIMIT 5;

Link Text :[data- 13.csv](https://github.com/user-attachments/files/19721934/data-.13.csv)


# (14). Player Who Conceded Most_Four_Per_Inning By An Individual Player Against IPL Franchies with their Runs And Match Date Since 2008 to 2022.

SELECT Player
, Runs
, Fours
, Against
, Venue
, Match_Date
FROM Most_Four_Per_Inning
WHERE Fours = (SELECT MAX(Fours) FROM Most_Four_Per_Inning);

Link Text :[data- 14.csv](https://github.com/user-attachments/files/19721936/data-.14.csv)


# (15). Bowler Who Conceded Most Runs In IPL Edition Since 2008 to 2022.

SELECT Player
, Runs
, Wkts
, Against
, Venue 
, Match_Date
FROM Most_Run_Conceded_Per_Inn
WHERE Runs = (SELECT MAX(Runs) FROM Most_Run_Conceded_Per_Inn);

Link Text :[data- 15.csv](https://github.com/user-attachments/files/19721941/data-.15.csv)


# (16). List of Player with Most Runs, Wkts, Against  at The Wankhede Stadium in IPL.

SELECT Player
, Runs
, Wkts
, Against
, Venue 
, Match_Date
FROM Most_Run_Conceded_Per_Inn
WHERE Runs  >= '50' AND Venue = 'Wankhede Stadium'
ORDER BY Runs DESC;

Link Text :[data-16.csv](https://github.com/user-attachments/files/19721949/data-16.csv)


# (17). Bowler Who Conceded Most Runs With Most Dot Ball in IPL Since 2008 to 2022.

SELECT Most_Run_Conceded_Per_Inn.Player
, Most_Run_Conceded_Per_Inn.Runs
, Most_Dot_Balls_Inning.Dots
, Most_Dot_Balls_Inning.Against
, Most_Dot_Balls_Inning.Venue
, Most_Dot_Balls_Inning.Match_Date
FROM Most_Dot_Balls_Inning
INNER JOIN Most_Run_Conceded_Per_Inn
ON Most_Run_Conceded_Per_Inn.Player = Most_Dot_Balls_Inning.Player
WHERE Most_Run_Conceded_Per_Inn.Runs = (SELECT MAX(Most_Run_Conceded_Per_Inn.Runs) FROM Most_Run_Conceded_Per_Inn);

Link Text :[data- 17.csv](https://github.com/user-attachments/files/19721952/data-.17.csv)


# (18). Virat Kohli Hit Total Number of Four At M. Chinnaswamy Stadium. 

SELECT SUM(Fours) AS Total_Fours
, Player
FROM Most_Four_Per_Inning
WHERE Player = 'Virat Kohli' AND Venue = 'M. Chinnaswamy Stadium' 
GROUP BY Player;

Link Text :[data- 18.csv](https://github.com/user-attachments/files/19721958/data-.18.csv)


# (19). MS Dhoni( Yani Ki Mai 'Thala' ) Hits Maximum Number of Four Against RCB Whole The Strike Rate is Above '150' in IPL.

SELECT MAX(Fours) AS Maximum_Fours 
, Player
FROM Most_Four_Per_Inning
WHERE Player = 'MS Dhoni' AND (Against = 'RCB' OR SR >= '150')
GROUP BY Player;
Link Text : [data-19.csv](https://github.com/user-attachments/files/19722080/data-19.csv)


# (20). Find List of Player Who Runs MIN in IPL Against And Venue With UNION.
SELECT Player, Runs, Against, Venue, Match_Date FROM Fatest_Centuries WHERE Runs = (SELECT MIN(Runs) FROM Fatest_Centuries)
UNION
SELECT Player, Runs, Against, Venue, Match_Date FROM Fatest_Fifties WHERE Runs = (SELECT MIN(Runs) FROM Fatest_Fifties)
ORDER BY Against ASC;

Link Text :[data- 20.csv](https://github.com/user-attachments/files/19722094/data-.20.csv)


# (21). Pick Player Who Hit Highest_Run In A Single Over, With That Player States.

SELECT Player, Runs, BF, SR, Fours, Sixes, Against, Venue, Match_Date
FROM Most_Runs_Per_Over
WHERE Runs = (SELECT MAX(Runs) FROM Most_Runs_Per_Over);

Link Text :[data- 21.csv](https://github.com/user-attachments/files/19722110/data-.21.csv)


# (22). Player Who Hits 35 or More Than 35 Run in a Over.

SELECT Most_Runs.Player
, Most_Runs.Runs AS Total_Runs
, Most_Runs_Per_Over.Runs AS Per_Over_Runs
, Most_Runs_Per_Over.Fours AS Per_Over_Fours
, Most_Runs_Per_Over.Sixes AS Per_Over_Sixes
, Most_Runs_Per_Over.Against
, Most_Runs_Per_Over.Venue
, Most_Runs_Per_Over.Match_Date
FROM Most_Runs
INNER JOIN Most_Runs_Per_Over
ON Most_Runs.Player = Most_Runs_Per_Over.Player
WHERE Most_Runs_Per_Over.Runs >= '35'
ORDER BY Per_Over_Runs DESC;

Link Text :[data- 22.csv](https://github.com/user-attachments/files/19722112/data-.22.csv)


# (23). List Out Player who hit maximum Sixes since 13-05-2014 to 28-05-2014.

SELECT Player 
, Runs
, BF
, SR
, Fours
, Sixes
, Against
, Venue
, Match_Date
FROM Most_Sixes_Per_Inn
WHERE Match_Date >= '2014-05-13' AND Match_Date <= '2014-05-28'
ORDER BY Sixes DESC
LIMIT 5;

Link Text :[data- 23.csv](https://github.com/user-attachments/files/19722113/data-.23.csv)


# (24). Player Who Hit's Maximum Sixes in a single Inning Since 2021.

SELECT Player 
, Runs
, BF
, SR
, Fours
, Sixes
, Against
, Venue
, Match_Date
FROM Most_Sixes_Per_Inn
WHERE Match_Date >= '2021-05-01' AND Match_Date <= '2021-10-02'
ORDER BY Sixes DESC
LIMIT 1;

Link Text :[data- 24.csv](https://github.com/user-attachments/files/19722114/data-.24.csv)


# (25). List OUT Plauyer who Hit's Maximum Number of fours and sixes Against With Venue In 2016.

SELECT Most_Sixes_Per_Inn.Player 
, Most_Four_Per_Inning.Fours
, Most_Sixes_Per_Inn.Sixes
, Most_Four_Per_Inning.Against
, Most_Sixes_Per_Inn.Venue
, Most_Four_Per_Inning.Match_Date
FROM Most_Sixes_Per_Inn
INNER JOIN Most_Four_Per_Inning
ON Most_Sixes_Per_Inn.Player = Most_Four_Per_Inning.Player
WHERE Most_Four_Per_Inning.Match_Date >= '2016-04-17' AND Most_Four_Per_Inning.Match_Date <= '2016-05-07'
ORDER BY Sixes DESC
LIMIT 5;

Link Text :[data- 25.csv](https://github.com/user-attachments/files/19722116/data-.25.csv)


# (26). Find Out A Player Who Make Fatest Centuries in 2021 With Their States.

SELECT Player
, Runs
, BF
, Fours
, Sixes
, Against
, Venue
, Match_Date
FROM Fatest_Centuries
WHERE Match_Date >= '2021-05-01' AND Match_Date <= '2021-10-02'
ORDER BY Sixes DESC
LIMIT 1; 

Link Text :[data- 26.csv](https://github.com/user-attachments/files/19722122/data-.26.csv)


# (27). Find Out A Player Who Hits Maximum Number of sixes in Single Inning's in IPL Season 2010.

SELECT Most_Runs.Player
, Most_Runs.Runs
, Fatest_Centuries.Fours
, Fatest_Centuries.Sixes
, Fatest_Centuries.Against
, Fatest_Centuries.Match_Date
FROM Fatest_Centuries
JOIN Most_Runs
ON Fatest_Centuries.Player = Most_Runs.Player
WHERE Match_Date >= '2010-04-03' AND Match_Date <= '2010-04-09'
ORDER BY Sixes DESC
LIMIT 1; 

Link Text :[data- 27.csv](https://github.com/user-attachments/files/19722124/data-.27.csv)
