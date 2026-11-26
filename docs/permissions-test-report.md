

\# CloudByte Permissions Test Report: Section 2



Date: 2026-11-26



\## Test Results



| User | Action | Expected | Observed |

|---|---|---|---|

| alice | Create a file in /shared/engineering | allow | allow; file inherited group engineering |

| alice | Create a new file in engineering | group engineering | group engineering (setgid) |

| emma | Write to /shared/dropbox | allow | allow |

| emma | List /shared/dropbox | deny | deny (sticky-bit dropbox permissions) |

| - | Check engineering files group | engineering | all files have group engineering |

| - | Check marketing files group | marketing | all files have group marketing |

| - | Check operations files group | operations | all files have group operations |



\## Directory Permissions



| Path | Owner:Group | Mode |

|---|---|---|

| /shared/engineering | root:engineering | 2770 |

| /shared/marketing | root:marketing | 2770 |

| /shared/operations | root:operations | 2770 |

| /shared/dropbox | root:admins | 1773 |



\## Verification



The verification script was executed successfully.



```text

=== Results: 18 passed, 0 failed ===

```



All 18 checks passed.



The five required file extensions were present:

.txt, .conf, .csv, .log, .sh



The file /shared/engineering/api.log contained the word ERROR.



\## Notes



\- Setgid ensures that new files inherit the team's group.

\- Sticky bit prevents non-owners from deleting other users' files in the dropbox.

\- The dropbox allows non-admin users to write but prevents them from listing its contents.

\- The verification script confirmed all Section 2 requirements.



