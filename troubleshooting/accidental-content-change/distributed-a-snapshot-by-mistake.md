# Distributed a snapshot by mistake

When you distribute a snapshot to one or more instances, then two things happen:   
  
1. Nuvolos will create a backup snapshot of the current state of all target instances and store this backup snapshot in the corresponding target instance.

2. All files, tables, and applications in the snapshot being distributed will be added to the existing content of the current state of each of the target instances. 

If you have accidentally distributed a snapshot, and you want to revert this operation, you can restore the backup snapshot created for each target instance when the distribution operation was performed. If the user has no permission to restore the snapshot in a target instance, she can contact the editor of that instance and ask him to restore the backup snapshot.

