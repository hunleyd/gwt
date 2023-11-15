
[![GPLv2 License](https://img.shields.io/badge/License-GPL%20v2-yellow.svg)](https://opensource.org/licenses/)
# gwt - a Git worktree wrapper

`gwt` is a Bash function to make working with [git worktree](https://git-scm.com/docs/git-worktree) a little easier. It provides functionality for listing all existing worktrees, creating new worktrees, removing stale worktrees, and automates updating a worktree upon entering it.

## Environment Variables

To run this project, you will need to add the following environment variables to your .env file

`GWT_REPO_HOME`

## Usage/Examples

### Set up / Configuration

1. Tell `gwt` where your Git repos live
```sh
~ $ export GWT_REPO_HOME=/srv/repos
```
2. Load `gwt` into your current shell
```sh
~ $ source /path/to/gwt
```

### Usage

#### List all worktrees in all repositories

```sh
~ $ gwt
/srv/repos/demo
↳ ask_me_about_free_upgrades                       48f9fefb8 [ask_me_about_free_upgrades]
↳ because_it_zee_standard                          08885f5f8 [because_it_zee_standard]
↳ bye_bye_ssh_hello_tls                            96e7caa91 [bye_bye_ssh_hello_tls]
↳ clusters_have_names                              47441094e [clusters_have_names]
↳ compute_pg_defaults                              f17eb3306 [compute_pg_defaults]
↳ computed_processes                               b2b0f4b75 [computed_processes]
↳ development                                      05f001eee [development]
↳ etcd_api_v3                                      fb0c287e3 [etcd_api_v3]
↳ heap-2660                                        67ed98aa9 [heap-2660]
↳ heap-2661                                        0b00da61f [heap-2661]
↳ ini_mini_miti_mo                                 1317ffaa1 [ini_mini_miti_mo]
↳ int_int_baby                                     4b38207c0 [int_int_baby]
↳ lint_lint_baby                                   ae72361e5 [lint_lint_baby]
↳ make_fetch_happen_for_gretchen                   bb74fe721 [make_fetch_happen_for_gretchen]
↳ pls_get_fresh_with_me                            4f2b6579f [pls_get_fresh_with_me]
↳ prepare_this                                     9d011fd4e [prepare_this]
↳ raft_beta                                        6ac90e7a0 [raft_beta]
↳ repov2                                           5020895e3 [repov2]
↳ rhel_9                                           27c2c4cf6 [rhel_9]
↳ unlimited_cosmic_files__itty_bitty_living_space  257c64a34 [unlimited_cosmic_files__itty_bitty_living_space]
↳ use_the_modules_luke                             a3d0d96af [use_the_modules_luke]
↳ validate_patroni                                 bd13c04a6 [validate_patroni]
↳ what_does_inactive_even_mean                     fcdc9c36e [what_does_inactive_even_mean]
↳ what_is_a_default_anyway                         d9ef509b1 [what_is_a_default_anyway]
↳ wilson_and_me_on_a_raft                          6184f8da0 [wilson_and_me_on_a_raft]

/srv/repos/set_user
↳ v4_upgrade_note  6b385b2 [v4_upgrade_note]

/srv/repos/pgmonitor
↳ development  da0824c [development]
```

#### List all worktrees in a given repo

```sh
~ $ gwt ls demo
demo
↳ ask_me_about_free_upgrades                       48f9fefb8 [ask_me_about_free_upgrades]
↳ because_it_zee_standard                          08885f5f8 [because_it_zee_standard]
↳ bye_bye_ssh_hello_tls                            96e7caa91 [bye_bye_ssh_hello_tls]
↳ clusters_have_names                              47441094e [clusters_have_names]
↳ compute_pg_defaults                              f17eb3306 [compute_pg_defaults]
↳ computed_processes                               b2b0f4b75 [computed_processes]
↳ development                                      05f001eee [development]
↳ etcd_api_v3                                      fb0c287e3 [etcd_api_v3]
↳ heap-2660                                        67ed98aa9 [heap-2660]
↳ heap-2661                                        0b00da61f [heap-2661]
↳ ini_mini_miti_mo                                 1317ffaa1 [ini_mini_miti_mo]
↳ int_int_baby                                     4b38207c0 [int_int_baby]
↳ lint_lint_baby                                   ae72361e5 [lint_lint_baby]
↳ make_fetch_happen_for_gretchen                   bb74fe721 [make_fetch_happen_for_gretchen]
↳ pls_get_fresh_with_me                            4f2b6579f [pls_get_fresh_with_me]
↳ prepare_this                                     9d011fd4e [prepare_this]
↳ raft_beta                                        6ac90e7a0 [raft_beta]
↳ repov2                                           5020895e3 [repov2]
↳ rhel_9                                           27c2c4cf6 [rhel_9]
↳ unlimited_cosmic_files__itty_bitty_living_space  257c64a34 [unlimited_cosmic_files__itty_bitty_living_space]
↳ use_the_modules_luke                             a3d0d96af [use_the_modules_luke]
↳ validate_patroni                                 bd13c04a6 [validate_patroni]
↳ what_does_inactive_even_mean                     fcdc9c36e [what_does_inactive_even_mean]
↳ what_is_a_default_anyway                         d9ef509b1 [what_is_a_default_anyway]
↳ wilson_and_me_on_a_raft                          6184f8da0 [wilson_and_me_on_a_raft]
```

#### Create a new worktree

```sh
~ $ gwt create demo demo
gwt: Checking if upstream is a fetchable remote
gwt: Fetching remote: upstream
gwt: Checking if development is a valid head on upstream remote
gwt: Creating worktree
Preparing worktree (new branch 'demo')
branch 'demo' set up to track 'upstream/development'.
HEAD is now at eec1595f1 update readme and contrib (#2056)
gwt: Checking if this repo uses submodules
gwt: No submodules configured in this repo
/srv/repos/demo/.trees/demo $
```

#### Switch to an existing worktree

```sh
~ $ gwt demo
gwt: Found the demo worktree
gwt: Checking if a merge is in progress
gwt: A merge IS NOT in progress
gwt: Determining the worktree's branch revision
gwt: Local worktree's branch revision: eec1595f1e2cc682e831678b47691ed2e13c835b
gwt: Fetching info from remote: origin
gwt: Checking if this branch exists on remote: origin
gwt: This worktree's branch not found on remote: origin
gwt: Determining the upstream remote for this branch
gwt: Determined the upstream remote for this branch: upstream
gwt: Determining the upstream branch for this branch
gwt: Determined the upstream branch for this branch: development
gwt: Fetching info from remote: upstream
gwt: Checking if upstream/development has advanced since last pull
gwt: Remote head has not advanced
/srv/repos/demo/.trees/demo $
```

#### Switch to a worktree where upstream has advanced
```sh
~ $ gwt heap-2660
gwt: Found the heap-2660 worktree
gwt: Checking if a merge is in progress
gwt: A merge IS NOT in progress
gwt: Determining the worktree's branch revision
gwt: Local worktree's branch revision: 67ed98aa9b2457d1ffede13545276fd7f0b57c1f
gwt: Fetching info from remote: origin
gwt: Checking if this branch exists on remote: origin
gwt: Checking the revision of this branch on: origin
gwt: Remote origin has this branch on revision: 67ed98aa9b2457d1ffede13545276fd7f0b57c1f
gwt: Checking the base revision of this branch on: origin
gwt: Revisions match; continuing
gwt: Determining the upstream remote for this branch
gwt: Determined the upstream remote for this branch: upstream
gwt: Determining the upstream branch for this branch
gwt: Determined the upstream branch for this branch: development
gwt: Fetching info from remote: upstream
gwt: Checking if upstream/development has advanced since last pull
gwt: Merging from remote head: upstream/development
/srv/repos/demo/.trees/heap-2660 $
```

#### Switch to a worktree with unpushed local commits

```sh
~ $ gwt heap-2660
gwt: Found the heap-2660 worktree
gwt: Checking if a merge is in progress
gwt: A merge IS NOT in progress
gwt: Determining the worktree's branch revision
gwt: Local worktree's branch revision: 36d59ff8d56a86e402a99f9c6ce3746c36643fd8
gwt: Fetching info from remote: origin
gwt: Checking if this branch exists on remote: origin
gwt: Checking the revision of this branch on: origin
gwt: Remote origin has this branch on revision: 67ed98aa9b2457d1ffede13545276fd7f0b57c1f
gwt: Checking the base revision of this branch on: origin
gwt: Pushing to remote: origin
gwt: Determining the upstream remote for this branch
gwt: Determined the upstream remote for this branch: upstream
gwt: Determining the upstream branch for this branch
gwt: Determined the upstream branch for this branch: development
gwt: Fetching info from remote: upstream
gwt: Checking if upstream/development has advanced since last pull
gwt: Merging from remote head: upstream/development
Already up to date.
/srv/repos/demo/.trees/heap-2660 $
```

#### Remove a worktree

```sh
~ $ gwt prune demo demo
gwt: Removing the worktree from disk: /srv/repos/demo/.trees/demo
gwt: Deleting the branch: demo
Deleted branch demo (was eec1595f1).
~ $
```
## License

[GPLv2](https://choosealicense.com/licenses/gpl-2.0/)

