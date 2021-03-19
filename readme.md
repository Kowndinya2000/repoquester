# Steps to run the tool RepoQuester
> 1. Install python libraries
````
pip -r requirements.txt
````
> 2. Download ```cloc```
````
https://github.com/AlDanial/cloc/tree/1.88#install-via-package-manager
````
> 3. Download ```Ack```
```
https://beyondgrep.com/install/
```
> 4. Open the file ```repo_urls``` 
````
Add username/repositoryname in newlines. 
A sample of 265 repository urls are present already in the file.
````
> 5. Open the file ```repo_languages``` 
````
Add repository's programming language in newlines. 
A sample of 265 repository languages are present already in the file.
````
> 6. Open the file ```repo_ids``` 
````
A sample of 265 repository ids are present already in the file.
To generate ids automatically, run the command: python3 generate_ids.py
````
> 7. Open the file ```tokens.py``` 
````
Alteast provide one Github Personal Access Token. 
Format to provide token can be viewed in the file.
````

> 8. Initialize the database
````
chmod +x *sh
sed -i -e 's/\r$//' initialize.sh
./initialize.sh
````
> 9. Run the script to analyze the repositories
````
./run.sh
````
> 10. Check the results in the database file ```repo_quester.db```

> 11. To re-run the analysis without modyfing repository information
````
chmod +x *sh
./clean.sh
./run.sh
````
> 12. To empty the repository information and results.
````
chmod +x *sh
./empty.sh
(This also deletes the database file. Only retains the usable tool template)
Follow the steps 4-9 again.  
````
> 13. To run a particular repository.
````
For example, to analyze repository with repo_id = 2 : run the below two commands
chmod +x script2.sh
./script2.sh
````
## Commands to query the database (refer to file connect.py to refer to schema)
> Open the file ```repo_quester.db``` 
>> Database file could be viewed in DB Browser for SQLite (download link: https://sqlitebrowser.org/)
>>> Table: ```repoquester_results```

> 14. To select a repository "Microsoft/IEDiagnosticsAdapter" use the below command: 
````
SELECT * FROM repoquester_results WHERE repository in ("Microsoft/IEDiagnosticsAdapter");
````
![Command Cell](https://kowndinya2000.github.io/repo-quester-resources.github.io/sql_command_cell.png)

> 15. To select a set of metrics for the repository "Microsoft/IEDiagnosticsAdapter" 
>> For example, to select metrics: community, continuous_integration and license use the below command:
````
SELECT community,continuous_integration,license FROM repoquester_results WHERE repository in ("Microsoft/IEDiagnosticsAdapter");
````
> 16. The results table can be exported to ```CSV```, ```JSON``` and ```sql``` file formats 
````
In the DB Browser for SQLite application:
Click on File->Export-> Database to SQL file
                     -> Table(s) as CSV file
                     -> Table(s) to JSON
````
![Export Results](https://kowndinya2000.github.io/repo-quester-resources.github.io/export2.png)



