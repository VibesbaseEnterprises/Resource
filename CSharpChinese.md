#开发规范

### 代码命名
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
- 所有临时变量、方法变量应采用 小骆驼式命名法（camelCase）命名方式，也就是首字母小写
-  **私有变量建议以 _ 开头并采用 小骆驼式命名法（camelCase）命名方式** 
- 所有的接口应以 I 单词开头
- 所有选项类应以 Options 结尾
- 所有筛选器应以 Filter 结尾
- 所有的帮助类应以 Helper 结尾
- 所有的拓展类应以 Extension 结尾

- 常量建议采用全字母大写命名方式，相连单词采用 _ 连接，如：APP_CONFIG_FILENAME

```
// Correct
public const string ShippingType = "DropShip";
public const string SHIPPING_TYPE = "DropShip";
// Avoid
public const string SHIPPINGTYPE = "DropShip";
```

-  两个字母的缩写全部大写，超过2个的采用Pascal命名方法

```
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer, fastFtpTransfer;
UIControl uiControl, nextUIControl;
```
- 不要用下划线分隔单词，除非是公开常量

```
// Correct
public DateTime clientAppointment;
public TimeSpan timeLeft;    

// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left; 
// Exception (Class field)

private DateTime _registrationDate;
public const string SHIPPING_TYPE = "DropShip";
```


- 避免使用缩写。除非通常用作名称的缩写，如Id、Xml、Ftp、Uri。

- 类名、接口名尽量用名词或者名词+形容词

- 对于局部、参数和成员声明，请使用预定义的类型名（C#别名），如int、float、string。

- 对局部变量声明使用隐式类型var。除非基本类型（int、string、double等）

- 根据源文件的主类来命名文件名，partial类的文件名使用类名用.连接它们的来源或用途，例如

```
// Located in Task.cs
public partial class Task
{
}
// Located in Task.generated.cs
public partial class Task
{
}

```

- 请垂直对齐大括号
// Correct

```
class Program
{
  static void Main(string[] args)
  {
    //...
  }
}
```


- 在类的顶部声明所有成员变量，静态变量在最顶部。
```
public class Account
{
  public static string BankName;
  public static decimal Reserves;      
  public string Number { get; set; }
  public DateTime DateOpened { get; set; }
  public DateTime DateClosed { get; set; }
  public decimal Balance { get; set; }     
  // Constructor
  public Account()
  {
    // ...
  }
}
```
- Enum使用单数名称。除非byte字段枚举。
```
// Correct
public enum Color
{
  Red,
  Green,
  Blue,
  Yellow,
  Magenta,
  Cyan
} 
// Exception
[Flags]
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```
- 不要显式指定枚举类型或枚举值（Bit字段除外）
```
// Don't
public enum Direction : long
{
  North = 1,
  East = 2,
  South = 3,
  West = 4
} 
// Correct
public enum Direction
{
  North,
  East,
  South,
  West
}
```
- Enum名不要加上enum或者flags
// Don't

```
[Flags]
public enum DockingsFlags
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
// Correct
[Flags]
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```
- 使用Any、Is、Have或类似的关键字前缀识符bool变量或者返回bool结果的方法

```
// Correct
public static bool IsNullOrEmpty(string value) {
    return (value == null || value.Length == 0);
}

```


### 文件命名
- 所有可程序执行文件名均采用大骆驼式命名法（Camel-Case），也就是首字母大写，如 MyServiceFile.cs
- 所有非程序执行文件名均采用全字母小写命名法，如 appsetting.json
- 文件命名尽量采用英语单词组成，并且具有意义的命名，如：AppConfigure.cs
- 不推荐任何缩写命名方式，如：AC.cs
- 所有的接口文件名应以 I单词开头
- 文件命名格式应遵循：{占位符}{修饰词}{名词}{类型}规范，如：IWarehouseServiceApiFilter

### 代码注释
- 类文件头建议加上copyright注释，标记版权说明及创建人和创建日期(可配置编辑器创建新类模板)

```
//=====================================================================================
//   Filename:  $safeitemname$
//
//   Description:  
//
//       Version:  1.0
//       Created:  $time$
//      Compiler:  vs2013 $clrversion$ 
//
//        Author:  $username$
//       company:  Xxy
//     Copyright:  $year$ $username$
//=====================================================================================

```

- 公开类/工具类必须注释类的用途和目的，并附带主要用法<example></example>
```
    /// <summary>
    /// Web element of type Select
    /// </summary>
    /// <example>
    /// Select an element by text
    /// <code lang="vbs">	
    /// driver.FindElementById("select").AsSelect.SelectByText "Option Two"
    /// </code>
    /// </example>
    public class SelectElement
    {
        
    }
```
- 公开方法必须标记方法说明、参数及返回值，特别注意的地方标记上<remarks>，方法会返回异常必须标记上<exception></exception>

```
        /// <summary>
        /// Return a number parsed from the text
        /// </summary>
        /// <param name="decimalCharacter">Decimal character. Default is "."</param>
        /// <param name="errorValue">Default value in case of failure</param>
        /// <returns>Number or defualt value</returns>
        /// <remarks>When given "foo" this method will deselect an option like:
        /// <para>
        /// &lt;option value="foo"&gt;Bar&lt;/option&gt;
        /// </para>
        /// </remarks>
        /// <exception cref="Errors.InvalidOperationError">Thrown when attempting to deselect all options from a SELECT 
        /// that does not support multiple selections.</exception>
```

- 方法代码段内注释用//，代码段外用///，

- 使用编辑器的注释功能添加代码段的注释，避免使用/* */注释多行代码

-  **代码功能未完成请标记上//Todo:注释** 
