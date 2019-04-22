---
title: 'CA2302: Festlegung von BinaryFormatter.Binder vor dem Aufruf von BinaryFormatter.Deserialize sicherstellen'
ms.date: 04/05/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fb997d8184ea9459b46eee95bfe2863e8c1c6ed0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59367288"
---
# <a name="ca2302-ensure-binaryformatterbinder-is-set-before-calling-binaryformatterdeserialize"></a>CA2302: Festlegung von BinaryFormatter.Binder vor dem Aufruf von BinaryFormatter.Deserialize sicherstellen

|||
|-|-|
|TypeName|EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize|
|CheckId|CA2302|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Deserialisierungsmethode war aufgerufen oder referenziert werden und die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> Eigenschaft kann null sein.

## <a name="rule-description"></a>Regelbeschreibung

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Diese Regel sucht nach <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Methoden- oder Verweise, die Deserialisierung bei <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> bei dessen <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> kann null sein. Wenn Sie Deserialisierung mit unterbinden möchten <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> unabhängig von der <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> -Eigenschaft, deaktivieren Sie diese Regel und [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md), und aktivieren Sie die Regel [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Wenn möglich, verwenden Sie stattdessen einen sicheren Serialisierer und **nicht es Angreifern ermöglichen, geben Sie einen beliebigen Typ zum Deserialisieren**. Einige Serialisierungsprogramme sicherer gehören:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Verwenden Sie niemals <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Wenn Sie einen Typresolver verwenden müssen, müssen Sie die deserialisierte Typen einer erwarteten Liste einschränken.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Verwenden Sie NewtonSoft Json.NET - TypeNameHandling.None. Wenn Sie einen anderen Wert für TypeNameHandling verwenden müssen, müssen Sie die deserialisierte Typen einer erwarteten Liste einschränken.
  - Protokollpuffer
- Stellen Sie die serialisierten Daten Manipulationssicheres. Melden Sie kryptografisch nach der Serialisierung die serialisierten Daten. Überprüfen Sie vor der Deserialisierung der kryptografischen Signatur. Sie müssen verhindern, dass die kryptografischen Schlüssel offengelegt werden und sollten für den Schlüsselrotationen entwerfen.
- Deserialisierte Typen zu beschränken. Implementieren Sie einen benutzerdefinierten <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Vor der Deserialisierung mit <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>legen die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> Eigenschaft, um eine Instanz des benutzerdefinierten <xref:System.Runtime.Serialization.SerializationBinder>. In der überschriebenen <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> -Methode, wenn der Typ wird dann eine Ausnahme auslöst.
  - Stellen Sie sicher, dass alle Codepfade haben die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> Eigenschaftensatz.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

- Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn Sie wissen, dass die Eingabe als vertrauenswürdig eingestuft wird. Beachten Sie, dass es sich bei Ihrer Anwendung Vertrauenswürdigkeit Grenze und Datenfluss im Laufe der Zeit ändern können.
- Es ist sicher, diese Warnung zu unterdrücken, wenn Sie eines der oben genannten Vorsichtsmaßnahmen ergriffen haben.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BinaryFormatter Formatter { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Property Formatter As BinaryFormatter

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Lösung
```csharp
using System;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", "typeName");
        }
    }
}

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        formatter.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Runtime.Serialization.Formatters.Binary

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", "typeName")
        End If
    End Function
End Class

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        formatter.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Verwandte Regeln

[CA2300: Verwenden Sie keine unsicheren Deserialisierer BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2301: Rufen Sie BinaryFormatter.Deserialize nicht ohne die erste Einstellung BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)
