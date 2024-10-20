Storing the block required for successful decryption in a separate block or file

Checking the execution time: Uses performance.now() or Date.now() to compare execution times

Logging the sequence of executed functions: Here, malware behaves differently if the sequence has changed;

Redefining the functions used in dynamic analysis: A good example of this can be a redefinition of the console.log function:

window\['console'\]\['log'\] = <other_function>;

Alternatively, it is possible to redefine the function as follows:

var console = {};
console.log = <other_function>;

Detection of developer tools: There are multiple ways it can be implemented, for example by checking windows' inner and outer sizes.