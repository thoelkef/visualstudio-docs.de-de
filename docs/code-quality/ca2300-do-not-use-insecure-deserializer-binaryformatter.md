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
ms.openlocfilehash: 400c259cf7aac5b6f3ea4a6c196ebaa77e29289b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079635"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300: Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Deserialisierungsmethode war aufgerufen oder referenziert werden.

## <a name="rule-description"></a>Regelbeschreibung

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Diese Regel sucht nach <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Deserialisierung Methoden- oder Verweise. Wenn Sie nur, wenn deserialisieren möchten die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> -Eigenschaftensatz auf Typen beschränken, deaktivieren diese Regel aus, und Aktivieren von Regeln [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) und [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) stattdessen.

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
- Wenn Sie die deserialisierte Typen beschränken, sollten Sie mit dieser Regel zu deaktivieren und Aktivieren von Regeln [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) und [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Regeln [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) und [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) Hilfe, um sicherzustellen, dass die <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> vor der Deserialisierung wird stets Eigenschaft festgelegt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

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

[CA2301: Rufen Sie BinaryFormatter.Deserialize nicht ohne die erste Einstellung BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Sicherstellen Sie, dass BinaryFormatter.Binder festgelegt ist, vor dem Aufrufen von BinaryFormatter.Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)