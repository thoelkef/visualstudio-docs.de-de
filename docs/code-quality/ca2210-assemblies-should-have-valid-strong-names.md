---
title: 'CA2210: Assemblys müssen gültige starke Namen aufweisen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e596f2e970df487a31628ab0bd29051172b950e4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931077"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Assemblys müssen gültige starke Namen aufweisen.

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Assembly ist nicht mit einem starken Namen signiert werden. der starke Name konnte nicht überprüft werden, oder der starke Name nicht gültig ist, ohne die aktuellen registrierungseinstellungen für die des Computers.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel abgerufen und überprüft den starken Namen einer Assembly. Eine Verletzung auftritt, wenn eine der folgenden Bedingungen zutrifft:

- Die Assembly keinen starken Namen.

- Die Assembly wurde nach der Anmeldung geändert werden.

- Die Assembly wird verzögert signiert.

- Die Assembly wurde nicht ordnungsgemäß signiert oder die Anmeldung ist fehlgeschlagen.

- Die Assembly benötigt, registrierungseinstellungen, Überprüfung übergeben wird. Beispielsweise wurde Strong Name-Tool (Sn.exe) verwendet, um die Überprüfung für die Assembly zu überspringen.

Der starke Name schützt Clients vor dem versehentlichen Laden einer manipulierten Assembly. Assemblys ohne starke Namen sollten nur in ganz bestimmten Szenarien bereitgestellt werden. Wenn Sie nicht einwandfrei signierte Assemblys freigeben oder verteilen, kann die Assembly manipuliert werden, die Common Language Runtime lädt die Assembly unter Umständen nicht, oder der Benutzer muss die Überprüfung auf dem Computer deaktivieren. Eine Assembly ohne starken Namen hat die folgenden Nachteile auf:

- Dessen Ursprung können nicht überprüft werden.

- Die common Language Runtime kann keine Benutzer zu warnen, wenn der Inhalt der Assembly geändert wurde.

- Es kann nicht im globalen Assemblycache geladen werden.

Beachten Sie, bis alles geladen und eine mit Verzögerung signierten Assembly analysieren, müssen Sie die Überprüfung der Assembly deaktivieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

### <a name="create-a-key-file"></a>Erstellen einer Schlüsseldatei

Verwenden Sie eine der folgenden Verfahren:

- Verwenden Sie das Assembly Linker-Tool (Al.exe) an, die von .NET Framework SDK bereitgestellten.

- Für die .NET Framework v1. 0 oder v1. 1, verwenden Sie entweder die <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> oder <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> Attribut.

- Für die [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], verwenden Sie entweder die `/keyfile` oder `/keycontainer` Compileroption [/keyfile (Geben Sie Schlüssel oder Schlüsselpaar zum Signieren einer Assembly)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) oder  [ /keycontainer (Geben Sie einen Schlüsselcontainer zum Signieren einer Assembly)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) -Linkeroption in C++).

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Signieren von Assemblys mit einem starken Namen in Visual Studio

1. Öffnen Sie in Visual Studio Ihre Projektmappe ein.

2. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften.**

3. Klicken Sie auf die **Signierung** , und wählen Sie die **Assembly signieren** Kontrollkästchen.

4. Von **Schlüsseldatei mit starkem Namen auswählen**Option **neu**.

   Die **Schlüssel für einen starken Namen erstellen** Fenster angezeigt.

5. In **Schlüsseldateiname**, geben Sie einen Namen für Ihre Schlüssel mit starkem Namen.

6. Wählen Sie, ob der Schlüssel mit einem Kennwort geschützt, und klicken Sie dann auf **OK**.

7. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **erstellen**.

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Signieren von Assemblys mit einem starken Namen außerhalb von Visual Studio

Verwenden Sie das strong Name-Tool (Sn.exe), das von .NET Framework SDK bereitgestellt wird. Weitere Informationen finden Sie unter [Sn.exe (Strong Name-Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie nur eine Warnung dieser Regel auf, wenn die Assembly in einer Umgebung verwendet wird, den Inhalt manipulieren nicht relevant ist.

## <a name="see-also"></a>Siehe auch

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [Vorgehensweise: Signieren einer Assembly mit einem starken Namen](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (Strong Name-Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool)