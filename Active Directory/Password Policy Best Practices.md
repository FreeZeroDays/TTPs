# Password Policy Best Practies
1. Configure a minimum password length (Personally I like 12 characters minimum but I know this changes from place to place). 
2. Enforce password history policy with at least 10 previous passwords remembered.
3. Enable the setting that requires passwords to meet complexity requirements.
4. Set a minimum password age of 3 days (Again, this is something that I know a lot of places like to change, I have seen 1 day be the lowest but like 3 personally).
5. Set a maximum password age (Something that is again up for debate, some places choose not to enforce this setting but I like 30 days). 
6. Enforce separate requirements for Domain Administrator passwords - a good example of this is 15 characters minimum. 
7. Reference: https://www.netwrix.com/account_lockout_best_practices.html

# Account Lockout Best Practices
1. Account lockout duration: 1440 minutes
2. Account lockout threshold: 5 invalid logon attempts
3. Reset account lockout after: 0 minutes [account does not unlock automatically]
4. Reference: https://www.netwrix.com/account_lockout_best_practices.html

# CIS Benchmarks as a Reference
* Minimum password length: 14
* Enforce Password History: 24
* Maximum password age: 60 or fewer days
* Minimum password age: 1 or more
* Password must meet complexity: Enabled
* Store passwords using reversible encryption: Disabled
* Account lockout threshold: Up to 10, but not 0
* Account lockout duration (minutes): 15 or more minutes
* Account lockout observation window (minutes): 30 minutes
