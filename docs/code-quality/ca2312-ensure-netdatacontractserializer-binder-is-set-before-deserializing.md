---
title: 'CA2312: Vor dem Deserialisieren sicherstellen, dass NetDataContractSerializer.Binder festgelegt ist'
ms.date: 05/01/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2312
- EnsureNetDataContractSerializerBinderIsSetBeforeDeserializing
ms.openlocfilehash: 38495a3c8d5a2efb5e5e96785cecbd6d50e9cd00
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891113"
---
# <a name="ca2312-ensure-netdatacontractserializerbinder-is-set-before-deserializing"></a>CA2312: Vor dem Deserialisieren sicherstellen, dass NetDataContractSerializer.Binder festgelegt ist

|||
|-|-|
|TypeName|EnsureNetDataContractSerializerBinderIsSetBeforeDeserializing|
|CheckId|CA2312|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Es <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> wurde eine Deserialisierungsmethode aufgerufen, auf <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> die verwiesen wird, und die-Eigenschaft kann NULL sein.

## <a name="rule-description"></a>Regelbeschreibung

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Diese Regel findet <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> deserialisierungsmethodenaufrufe oder Verweise <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> , wenn der möglicherweise NULL ist. Wenn <xref:System.Runtime.Serialization.NetDataContractSerializer> Sie die Deserialisierung unabhängig von der <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> Eigenschaft nicht zulassen möchten, deaktivieren Sie diese Regel und [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md), und aktivieren Sie die Regel [CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Verwenden Sie, wenn möglich, stattdessen ein sicheres Serialisierungsprogramm, und **lassen Sie nicht zu, dass ein Angreifer einen beliebigen zu deserialisierenden Typ angibt**. Zu den sichereren serialisierungssoren zählen:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Nie verwenden <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Wenn Sie einen Typresolver verwenden müssen, beschränken Sie deserialisierte Typen auf eine erwartete Liste.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft JSON.net: Verwenden Sie typamehandult. None. Wenn Sie einen anderen Wert für typamehanding verwenden müssen, beschränken Sie deserialisierte Typen auf eine erwartete Liste mit einem benutzerdefinierten iserializationbinder.
  - Protokollpuffer
- Sorgen Sie dafür, dass die serialisierten Daten manipuliert werden. Signieren Sie die serialisierten Daten nach der Serialisierung kryptografisch. Überprüfen Sie vor der Deserialisierung die kryptografische Signatur. Schützen Sie den Kryptografieschlüssel vor der Offenlegung, und entwerfen Sie Schlüssel Drehungen.
- Deserialisierte Typen einschränken. Implementieren Sie einen <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>benutzerdefinierten. Legen Sie die-Eigenschaft <xref:System.Runtime.Serialization.NetDataContractSerializer>vor der <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> Deserialisierung mit auf eine Instanz des <xref:System.Runtime.Serialization.SerializationBinder>benutzerdefinierten fest. Lösen Sie in der <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> überschriebenen Methode, wenn der Typ unerwartet ist, eine Ausnahme aus, um die Deserialisierung zu beenden.
  - Stellen Sie sicher, dass die <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> Eigenschaft für alle Codepfade festgelegt ist

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public NetDataContractSerializer Serializer { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Property Serializer As NetDataContractSerializer

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Lösung

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

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

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        serializer.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

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

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        serializer.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Verwandte Regeln

[CA2310: Nicht sicheres Deserialisierungsprogramm NetDataContractSerializer verwenden](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)

[CA2311: Nicht deserialisieren, ohne zuerst NetDataContractSerializer. Binder festzulegen](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)
