---
title: 'CA2300: Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden'
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
f1_keywords:
- CA2300
- DoNotUseInsecureDeserializerBinaryFormatter
ms.openlocfilehash: 4ca4990308ceab21e2c6e256770ff37a3ca9a6fc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237947"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300: Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Deserialisierungsmethode wurde aufgerufen oder referenziert.

## <a name="rule-description"></a>Regelbeschreibung

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Diese Regel findet <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> deserialisierungsmethodenaufrufe oder Verweise. Wenn Sie nur deserialisieren möchten, wenn die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> -Eigenschaft auf Typen beschränken festgelegt ist, deaktivieren Sie diese Regel, und aktivieren Sie stattdessen Rules [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) und [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Verwenden Sie, wenn möglich, stattdessen ein sicheres Serialisierungsprogramm, und **lassen Sie nicht zu, dass ein Angreifer einen beliebigen zu deserialisierenden Typ angibt**. Zu den sichereren serialisierungssoren zählen:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Nie verwenden <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Wenn Sie einen Typresolver verwenden müssen, beschränken Sie deserialisierte Typen auf eine erwartete Liste.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft JSON.net: Verwenden Sie typamehandult. None. Wenn Sie einen anderen Wert für typamehanding verwenden müssen, beschränken Sie deserialisierte Typen auf eine erwartete Liste mit einem benutzerdefinierten iserializationbinder.
  - Protokollpuffer
- Sorgen Sie dafür, dass die serialisierten Daten manipuliert werden. Signieren Sie die serialisierten Daten nach der Serialisierung kryptografisch. Überprüfen Sie vor der Deserialisierung die kryptografische Signatur. Schützen Sie den Kryptografieschlüssel vor der Offenlegung, und entwerfen Sie Schlüssel Drehungen.
- Deserialisierte Typen einschränken. Implementieren Sie einen <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>benutzerdefinierten. Legen Sie die-Eigenschaft <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>vor der <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> Deserialisierung mit auf eine Instanz des <xref:System.Runtime.Serialization.SerializationBinder>benutzerdefinierten fest. Lösen Sie in der <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> überschriebenen Methode, wenn der Typ unerwartet ist, eine Ausnahme aus, um die Deserialisierung zu beenden.
  - Wenn Sie deserialisierte Typen einschränken, empfiehlt es sich, diese Regel zu deaktivieren und Regeln [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) und [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)zu aktivieren. Mithilfe von Regeln [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) und [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) können Sie sicher <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> stellen, dass die Eigenschaft vor der Deserialisierung immer festgelegt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Pseudo Codebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Verwandte Regeln

[CA2301: Rufen Sie nicht BinaryFormatter. Deserialize auf, ohne zuerst BinaryFormatter. Binder festzulegen.](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Stellen Sie sicher, dass BinaryFormatter. Binder vor dem Aufrufen von BinaryFormatter. Deserialize festgelegt ist.](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)