---
title: "Unterstützung von NGen in VSIX v3 | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>Unterstützung von NGen in VSIX v3

Mit Visual Studio 2017 und die neue VSIX v3 (Version 3) Erweiterungsmanifest jetzt Erweiterung können Entwickler-Format "Ngen" ihre Assemblys bei der Installation.

Im folgenden ist ein Auszug aus MSDN, aus der hervorgeht, welche "Ngen" ist:

>Native Image Generator (Ngen.exe) ist ein Tool zur Leistungsoptimierung verwalteter Anwendungen. Mit "Ngen.exe" können Sie systemeigene Images erstellen, also Dateien mit kompiliertem prozessorspezifischem Computercode, die daraufhin im Cache für systemeigene Images auf dem lokalen Computer installiert werden. Die Laufzeit kann systemeigene Abbilder aus dem Cache nutzen und muss nicht den JIT (Just-In-Time)-Compiler verwenden, um die ursprüngliche Assembly zu kompilieren.
>
>aus [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Zu "Ngen" eine Assembly muss der VSIX-Datei installiert werden "pro Computer Instanzebene". Dies kann durch Aktivieren des Kontrollkästchens "All Users" im Designer extension.vsixmanifest aktiviert werden:

![Überprüfen Sie alle Benutzer](~/docs/extensibility/media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Gewusst wie: Aktivieren von Ngen

Um Ngen für eine Assembly zu aktivieren, können Sie die **Eigenschaften** in Visual Studio im Fenster.

Es gibt 4 Eigenschaften, die festgelegt werden können:

1. **NGen** (Boolean) – bei "true" Visual Studio-Installationsprogramm wird "Ngen" die Assembly.
2. **NGen-Anwendung** (Zeichenfolge) – Ngen bietet die Möglichkeit, die Datei app.config der Anwendung zu verwenden, um die Assemblyabhängigkeiten zu beheben. Dieser Wert sollte auf eine Anwendung, deren "App.config" (in Bezug auf die Visual Studio-Installationsverzeichnis) verwenden möchten, festgelegt werden.
3. **NGen-Architektur** (Enum) – die Architektur Ihrer Assembly systemintern kompilieren. Die Optionen sind: ein. B "NotSpecified". X86 c. X64 d. Alle
4. **NGen-Priorität** (ganze Zahl zwischen 1 und 3) – die Ngen-Priorität behandelt [Ngen.exe Prioritätsstufen](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Hier wird erläutert, die **Eigenschaften** Fenster in Aktion:

![NGen in Eigenschaften](~/docs/extensibility/media/ngen-in-properties.png)

Dies wird in der CSPROJ-Datei für das VSIX-Projekt den Projektverweis Metadaten hinzufügen:

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

 >**Hinweis:** Sie können auf Wunsch die CSPROJ-Datei direkt bearbeiten.

## <a name="extra-information"></a>Zusätzliche Informationen

Die Eigenschaft geändert, gelten für mehr als nur Verweise des Projekts. Sie können die Ngen-Metadaten für Elemente festlegen, in dem Projekt auch (mit der gleichen oben beschriebenen Methoden) so lange, wie die Elemente .NET-Assemblys sind.
