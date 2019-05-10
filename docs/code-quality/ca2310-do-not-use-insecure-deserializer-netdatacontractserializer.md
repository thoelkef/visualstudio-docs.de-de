---
title: 'CA2310: Verwenden Sie keine unsicheren Deserialisierer NetDataContractSerializer'
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
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135428"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Verwenden Sie keine unsicheren Deserialisierer NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> Deserialisierungsmethode war aufgerufen oder referenziert werden.

## <a name="rule-description"></a>Regelbeschreibung

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Diese Regel sucht nach <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> Deserialisierung Methoden- oder Verweise. Wenn Sie nur, wenn deserialisieren möchten die <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> -Eigenschaftensatz auf Typen beschränken, deaktivieren diese Regel aus, und Aktivieren von Regeln [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) und [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) stattdessen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Wenn möglich, verwenden Sie stattdessen einen sicheren Serialisierer und **nicht es Angreifern ermöglichen, geben Sie einen beliebigen Typ zum Deserialisieren**. Einige Serialisierungsprogramme sicherer gehören:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Verwenden Sie niemals <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Wenn Sie einen Typresolver verwenden müssen, beschränken Sie deserialisierte Typen einer erwarteten Liste aus.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Verwenden Sie Newtonsoft Json.NET - TypeNameHandling.None. Wenn Sie einen anderen Wert für TypeNameHandling verwenden müssen, beschränken Sie zu einer erwarteten Liste mit einem benutzerdefinierten ISerializationBinder deserialisierte Typen.
  - Protokollpuffer
- Stellen Sie die serialisierten Daten vor Manipulationen sicher. Melden Sie kryptografisch nach der Serialisierung die serialisierten Daten. Überprüfen Sie vor der Deserialisierung die kryptografische Signatur. Schützen Sie die kryptografischen Schlüssel vom offen gelegt wird und der Entwurf für die Schlüsselrotationen.
- Deserialisierte Typen zu beschränken. Implementieren Sie einen benutzerdefinierten <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Vor der Deserialisierung mit <xref:System.Runtime.Serialization.NetDataContractSerializer>legen die <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> Eigenschaft, um eine Instanz des benutzerdefinierten <xref:System.Runtime.Serialization.SerializationBinder>. In der überschriebenen <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> -Methode, wenn der Typ, wird eine Ausnahme auslösen.
- Wenn Sie die deserialisierte Typen beschränken, sollten Sie mit dieser Regel zu deaktivieren und Aktivieren von Regeln [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) und [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Regeln [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) und [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) Hilfe, um sicherzustellen, dass die <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> vor der Deserialisierung wird stets Eigenschaft festgelegt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Verwandte Regeln

[CA2311: Führen Sie nicht deserialisiert werden, ohne die erste Einstellung NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Stellen Sie sicher, dass vor der Deserialisierung NetDataContractSerializer.Binder festgelegt ist](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
