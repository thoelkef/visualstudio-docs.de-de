---
title: "NGen-Unterstützung in VSIX v3 | Microsoft Docs"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15277f0a1038e43bb316d604cbc415da4a5d80bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ngen-support-in-vsix-v3"></a>NGen-Unterstützung in VSIX v3

Mit Visual Studio 2017 und dem neuen v3-VSIX-manifest (Version 3)-Erweiterung jetzt Erweiterung können Entwickler-Format "Ngen" ihre Assemblys bei der Installation.

Im folgenden ist ein Auszug aus MSDN, aus der hervorgeht, welche "Ngen" ist:

>Native Image Generator (Ngen.exe) ist ein Tool zur Leistungsoptimierung verwalteter Anwendungen. Mit "Ngen.exe" können Sie systemeigene Images erstellen, also Dateien mit kompiliertem prozessorspezifischem Computercode, die daraufhin im Cache für systemeigene Images auf dem lokalen Computer installiert werden. Die Laufzeit kann systemeigene Abbilder aus dem Cache nutzen und muss nicht den JIT (Just-In-Time)-Compiler verwenden, um die ursprüngliche Assembly zu kompilieren.
>
>aus [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

In der Reihenfolge nach "Ngen" eine Assembly muss die VSIX installiert sein "pro Computer instanzweise". Dies kann aktiviert werden, indem Sie das Kontrollkästchen "alle Benutzer" im Designer "Extension.vsixmanifest" überprüfen:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Gewusst wie: Aktivieren von Ngen

Zum Aktivieren von Ngen für eine Assembly können Sie die **Eigenschaften** Fenster in Visual Studio.

Es sind 4 Eigenschaften, die festgelegt werden können:

1. **NGen** (Boolean) – bei "true", die Visual Studio-Installer wird "Ngen" die Assembly.
2. **NGen-Anwendung** (Zeichenfolge) – Ngen bietet die Möglichkeit, eine Anwendungsdatei "App.config" zu verwenden, um die Assemblyabhängigkeiten aufzulösen. Dieser Wert sollte auf eine Anwendung, deren "App.config" (in Bezug auf das Visual Studio-Installationsverzeichnis) verwenden möchten, festgelegt werden.
3. **NGen-Architektur** (Enum) - Architektur, die die Assembly nativ kompilieren. Die Optionen sind: ein. "NotSpecified" b. X86 c. X64 d. Alle
4. **NGen-Priorität** (ganze Zahl zwischen 1 und 3) – die Ngen-Prioritätsstufe behandelt [Ngen.exe Prioritätsstufen](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Hier bietet eine Übersicht über die **Eigenschaften** Fenster in Aktion:

![NGen in Eigenschaften](media/ngen-in-properties.png)

Dadurch wird der Projektverweis innerhalb des VSIX-Projekts CSPROJ-Datei Metadaten hinzugefügt:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Hinweis:** Sie können die CSPROJ-Datei direkt bearbeiten, falls gewünscht.

## <a name="extra-information"></a>Zusätzliche Informationen

Die Eigenschaft-Designers Änderungen gelten für mehr als nur Projektverweise; Sie können die Ngen-Metadaten für Elemente festlegen, in dem Projekt auch (mithilfe derselben Methoden, die oben beschriebenen) so lange, wie die Elemente .NET Assemblys sind.