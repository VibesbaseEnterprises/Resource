
#Exception Handling

For all functions except the inferface level, implement try catch and to capture the exception, and rethrow it with this wrap.

```

using UneedgoHelper.DotNet.Common;

try
{

}
 catch (Exception ex)
 {
       throw ExceptionUtility.WrapException(MethodBase.GetCurrentMethod(), ex, "OTHER MESSAGES HERE");
 }

``` 
