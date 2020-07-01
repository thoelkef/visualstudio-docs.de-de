---
title: 'CA2210: Assemblys müssen gültige starke Namen haben | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8f800a550717abfabdfb9296fc8f6de49d127d73
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548199"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Assemblys müssen gültige starke Namen aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Assembly ist nicht mit einem starken Namen signiert, der starke Name konnte nicht überprüft werden, oder der starke Name ist ohne die aktuellen Registrierungs Einstellungen des Computers nicht gültig.

## <a name="rule-description"></a>Beschreibung der Regel
 Mit dieser Regel wird der starke Name einer Assembly abgerufen und überprüft. Eine Verletzung tritt auf, wenn eine der folgenden Punkte zutrifft:

- Die Assembly hat keinen starken Namen.

- Die Assembly wurde nach der Signierung geändert.

- Die Assembly ist verzögert signiert.

- Die Assembly wurde falsch signiert, oder die Signierung ist fehlgeschlagen.

- Die Assembly benötigt Registrierungs Einstellungen, um die Überprüfung zu übergeben. Beispielsweise wurde das Strong Name-Tool (Sn.exe) verwendet, um die Überprüfung für die Assembly zu überspringen.

  Der starke Name schützt Clients vor dem versehentlichen Laden einer manipulierten Assembly. Assemblys ohne starke Namen sollten nur in ganz bestimmten Szenarien bereitgestellt werden. Wenn Sie nicht einwandfrei signierte Assemblys freigeben oder verteilen, kann die Assembly manipuliert werden, die Common Language Runtime lädt die Assembly unter Umständen nicht, oder der Benutzer muss die Überprüfung auf dem Computer deaktivieren. Eine Assembly ohne starken Namen hat folgende Nachteile:

- Seine Ursprünge können nicht überprüft werden.

- Der Common Language Runtime kann Benutzer nicht warnen, wenn der Inhalt der Assembly geändert wurde.

- Sie kann nicht in den globalen Assemblycache geladen werden.

  Beachten Sie, dass Sie die Überprüfung für die Assembly deaktivieren müssen, um eine verzögert signierte Assembly zu laden und zu analysieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 **So erstellen Sie eine Schlüsseldatei**

 Verwenden Sie eines der folgenden Verfahren:

- Verwenden Sie das vom SDK bereitgestellte Assembly Linker-Tool (Al.exe) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

- Verwenden Sie für [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v 1.0 oder v 1.1 entweder das- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> oder das- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> Attribut.

- [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]Verwenden Sie für das entweder die-oder die- `/keyfile` `/keycontainer` Compileroption [/keyfile (Schlüssel-oder Schlüsselpaar zum Signieren einer Assembly angeben)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) oder [/keycontainer (geben Sie einen Schlüssel Container zum Signieren einer Assembly an)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) die Linkeroption in C++).

  **So signieren Sie die Assembly mit einem starken Namen in Visual Studio**

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Öffnen Sie in die Projekt Mappe.

2. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften.**

3. Klicken Sie auf die Registerkarte **Signierung** , und aktivieren Sie das Kontrollkästchen **Assembly signieren** .

4. Wählen Sie unter **Schlüsseldatei mit starkem Namen auswählen**die Option **neu**aus.

    Das Fenster Schlüssel für einen **starken Namen erstellen** wird angezeigt.

5. Geben Sie unter **Schlüssel Dateiname**einen Namen für den Schlüssel ihres starken Namens ein.

6. Wählen Sie aus, ob der Schlüssel mit einem Kennwort geschützt werden soll, und klicken Sie dann auf **OK**.

7. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Erstellen**.

   **So signieren Sie die Assembly mit einem starken Namen außerhalb von Visual Studio**

- Verwenden Sie das Strong Name-Tool (Sn.exe), das vom SDK bereitgestellt wird [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Weitere Informationen finden Sie unter [Sn.exe (Strong Name-Tool)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt nur eine Warnung aus dieser Regel, wenn die Assembly in einer Umgebung verwendet wird, in der Manipulationen an den Inhalten nicht von Bedeutung sind.

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 Gewusst [wie: Signieren einer Assembly mit einem starken Namen](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (Strong Name-Tool)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
