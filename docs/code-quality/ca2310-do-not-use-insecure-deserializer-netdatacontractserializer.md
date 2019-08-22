---
title: 'CA2310: Unsicheren Deserialisierer nicht verwenden: NetDataContractSerializer'
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
ms.openlocfilehash: 09496fd11945ec4d419cc215569a7436f96d71ec
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891151"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Unsicheren Deserialisierer nicht verwenden: NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> Deserialisierungsmethode wurde aufgerufen oder referenziert.

## <a name="rule-description"></a>Regelbeschreibung

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Diese Regel findet <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> deserialisierungsmethodenaufrufe oder Verweise. Wenn Sie nur deserialisieren möchten, wenn die <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> -Eigenschaft auf Typen beschränken festgelegt ist, deaktivieren Sie diese Regel, und aktivieren Sie stattdessen Rules [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) und [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) .

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
  - Wenn Sie deserialisierte Typen einschränken, empfiehlt es sich, diese Regel zu deaktivieren und Regeln [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) und [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)zu aktivieren. Mithilfe von Regeln [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) und [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) können Sie sicher <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> stellen, dass die Eigenschaft vor der Deserialisierung immer festgelegt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

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

[CA2311: Nicht deserialisieren, ohne zuerst NetDataContractSerializer. Binder festzulegen](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Stellen Sie sicher, dass NetDataContractSerializer. Binder vor der Deserialisierung festgelegt ist.](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
