pes vcs lab report

q51
checkout needs to update head and swap files in the folder but its hard because you have to check if the user has unsaved stuff or youll just delet their work. its just a lot of recursive tree walking.

q52
you check if the index hash is diffrent from the head tree or if the disk file diffrs from the index stats to find dirty files.

q53
commits just float in the object store without a branch name so they get lost easily when you switch branches. you have to manualy find the hash to get them back.

q61
its just a mark and sweep starting from the refs. use a hash set to track stuff. with 100k commits you might visit millions of objects which sounds like a total drag to implement.

q62
gc might kill a new blob before the commit finishes linking it. git just waits two weeks before deleting anything to avoid that race condtion.
