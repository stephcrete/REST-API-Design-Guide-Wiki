When requests are sent to delete resources, there are basically two cases to consider:
* you want the resource deleted no matter what
* you only want the resource deleted if you had the up to date version

Again, the ETag can be of use here:
* provide the ETag with the delete request to state that the resource should only be deleted IF the provided ETag is the correct one
  * concrete example: you search for data based on a specific criteria and decide to delete an entry that matches your search; it could be that another user updated the data, making it different enough not to match your initial search criterias, meaning that you wouldn't have considered that item for deletion with this new state
* don't provide the ETag to state that it should be deleted whether it has changed or not
  * the back-end might also decide that the ETag is mandatory