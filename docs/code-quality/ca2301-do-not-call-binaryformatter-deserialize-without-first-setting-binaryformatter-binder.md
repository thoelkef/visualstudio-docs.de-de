---
title: 'CA2301: BinaryFormatter.Deserialize nicht ohne Festlegung von BinaryFormatter.Binder aufrufen'
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
ms.openlocfilehash: d90ed71c1d5ca4cbfdcf8e500e1d176519a2fdff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037595"
---
# <a name="ca2301-do-not-call-binaryformatterdeserialize-without-first-setting-binaryformatterbinder"></a>CA2301: BinaryFormatter.Deserialize nicht ohne Festlegung von BinaryFormatter.Binder aufrufen

|||
|-|-|
|TypeName|DoNotCallBinaryFormatterDeserializeWithoutFirstSettingBinaryFormatterBinder|
|CheckId|CA2301|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Deserialisierungsmethode war aufgerufen oder verwiesen wird, ohne die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> Eigenschaftensatz.

## <a name="rule-description"></a>Regelbeschreibung

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Diese Regel sucht nach <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Deserialisierung Methoden- oder Verweise auf, wenn <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> verfügt nicht über die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> festgelegt. Wenn Sie Deserialisierung mit unterbinden möchten <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> unabhängig von der <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> -Eigenschaft, deaktivieren Sie diese Regel und [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md), und aktivieren Sie die Regel [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Wenn möglich, verwenden Sie stattdessen einen sicheren Serialisierer und **nicht es Angreifern ermöglichen, geben Sie einen beliebigen Typ zum Deserialisieren**. Einige Serialisierungsprogramme sicherer gehören:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Verwenden Sie niemals <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Wenn Sie einen Typresolver verwenden müssen, beschränken Sie deserialisierte Typen einer erwarteten Liste aus.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Verwenden Sie NewtonSoft Json.NET - TypeNameHandling.None. Wenn Sie einen anderen Wert für TypeNameHandling verwenden müssen, beschränken Sie zu einer erwarteten Liste mit einem benutzerdefinierten ISerializationBinder deserialisierte Typen.
  - Protokollpuffer
- Stellen Sie die serialisierten Daten vor Manipulationen sicher. Melden Sie kryptografisch nach der Serialisierung die serialisierten Daten. Überprüfen Sie vor der Deserialisierung die kryptografische Signatur. Verhindern Sie, dass die kryptografischen Schlüssel offen gelegt wird und für den Schlüsselrotationen entwerfen.
- Deserialisierte Typen zu beschränken. Implementieren Sie einen benutzerdefinierten <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Vor der Deserialisierung mit <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>legen die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> Eigenschaft, um eine Instanz des benutzerdefinierten <xref:System.Runtime.Serialization.SerializationBinder>. In der überschriebenen <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> -Methode, wenn der Typ wird dann eine Ausnahme auslöst.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

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
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
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
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
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
            throw new ArgumentException("Unexpected type", nameof(typeName));
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
            Throw New ArgumentException("Unexpected type", NameOf(typeName))
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

[CA2302: Sicherstellen Sie, dass BinaryFormatter.Binder festgelegt ist, vor dem Aufrufen von BinaryFormatter.Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)