
**Replace eval with print**
Add eval = print; as the first line in the script. This redefines eval so that it prints the parameter being passed to eval, rather than executing it.

**Isolate the JS block**
Isolate the JavaScript block (everything within the \<script\> tags, but not including
the \<script\> tags) and place it into a separate file.