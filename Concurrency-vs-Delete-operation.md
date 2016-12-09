# About
When requests are sent to delete resources, there are basically two cases to consider:
* you want the resource deleted no matter what
* you only want the resource deleted if you had the up to date version

Again, the ETag can be of use here.

# Providing an ETag with a delete request
Provide the ETag with the delete request to state that the resource should only be deleted IF the provided ETag is the correct one.

Concrete example: you search for data based on a specific criteria and decide to delete an entry that matches your search; it could be that another user updated the data, making it different enough not to match your initial search criterias, meaning that you wouldn't have considered that item for deletion with this new state

# Not providing an ETag with a delete request
If you don't provide the ETag in a delete request, it means that the resource should be deleted whether it has changed or not.

The back-end might also decide that the ETag is mandatory and in that case it would return an 4xx error if you didn't specify the ETag.