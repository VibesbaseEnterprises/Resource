# C# Guideline

### Naming
| **Identifier** | **Casing** | **Example** |
| --- | --- | --- |
| Namespace | Pascal | namespace  **System** . **Security** { ... } |
| Type | Pascal | public class  **StreamReader** { ... } |
| Interface | Pascal | public interface  **IEnumerable** { ... } |
| Method | Pascal | public class Object {public virtual string  **ToString** ();} |
| Property | Pascal | public class String {public int  **Length** { get; }} |
| Event | Pascal | public class Process {public event EventHandler  **Exited** ;} |
| Public Field | Pascal | public class MessageQueue {public static readonly  **TimeSpanInfiniteTimeout** ;}public struct  **UInt32** {public const  **Min** = 0;} |
| Private Field | \_Camel | public class String {private int  **_length** ;} |
| Local variables | Camel | public class UserLog{public void Add(LogEvent logEvent){int itemCount = logEvent.Items.Count;// ...}} |
| Enum value | Pascal | public enum  **FileMode** { **Append** ,...} |
| Parameter | Camel | public class Convert {public static int ToInt32(string  **value** );} |

- 所有类、接口、方法、属性、委托、枚举、选项、筛选器等 Public 类型应采用大骆驼式命名法（CamelCase）命名方式
- All public of these use CamelCase: classes interface, method, property, delegate, enumeration, 
- 所有临时变量、方法变量应采用 小骆驼式命名法（camelCase）命名方式，也就是首字母小写
- 
-  **私有变量建议以 _ 开头并采用 小骆驼式命名法（camelCase）命名方式** 
- 所有的接口应以 I 单词开头
- 所有选项类应以 Options 结尾
- 所有筛选器应以 Filter 结尾
- 所有的帮助类应以 Helper 结尾
- 所有的拓展类应以 Extension 结尾
