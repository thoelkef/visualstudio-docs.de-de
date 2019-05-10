---
title: 'CA2210: Assemblys müssen gültige starke Namen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b286a67b21d022b12f77ffff68a71da88256757
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095775"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Assemblys müssen gültige starke Namen aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 **Um eine Schlüsseldatei zu erstellen.**

 Verwenden Sie eine der folgenden Verfahren:

- Verwenden Sie die Assembly Linker-Tool (Al.exe) gebotenen die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Für die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 1.0 und 1.1, verwenden Sie entweder die <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> oder <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> Attribut.

- Für die [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], verwenden Sie entweder die `/keyfile` oder `/keycontainer` Compileroption [/keyfile (Geben Sie Schlüssel oder Schlüsselpaar zum Signieren einer Assembly)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) oder  [ /keycontainer (Geben Sie einen Schlüsselcontainer zum Signieren einer Assembly)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) -Linkeroption in C++).

  **Zum Signieren der Assembly mit einem starken Namen in Visual Studio**

1. In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], öffnen Sie die Projektmappe.

2. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften.**

3. Klicken Sie auf die **Signierung** , und wählen Sie die **Assembly signieren** Kontrollkästchen.

4. Von **Schlüsseldatei mit starkem Namen auswählen**Option **neu**.

    Die **Schlüssel für einen starken Namen erstellen** Fenster angezeigt.

5. In **Schlüsseldateiname**, geben Sie einen Namen für Ihre Schlüssel mit starkem Namen.

6. Wählen Sie, ob der Schlüssel mit einem Kennwort geschützt, und klicken Sie dann auf **OK**.

7. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **erstellen**.

   **So signieren Sie Ihre Assembly mit einem starken Namen außerhalb von Visual Studio**

- Verwenden Sie das strong Name-Tool (Sn.exe), die von bereitgestellte der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Weitere Informationen finden Sie unter [Sn.exe (Strong Name-Tool)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie nur eine Warnung dieser Regel auf, wenn die Assembly in einer Umgebung verwendet wird, den Inhalt manipulieren nicht relevant ist.

## <a name="see-also"></a>Siehe auch
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Vorgehensweise: Signieren einer Assembly mit einem starken Namen](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (Strong Name-Tool)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
