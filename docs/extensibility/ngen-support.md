---
title: NGen-Unterstützung in VSIX v3 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2919559a748769c3b30e09023ad4f10965d62ce6
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639489"
---
# <a name="ngen-support-in-vsix-v3"></a>NGen-Unterstützung in VSIX v3

Die neuen VSIX v3 mit Visual Studio 2017 (Version 3) Erweiterungsmanifest Format Erweiterung Entwickler können jetzt "Ngen" die Assemblys bei der Installation.

Im folgenden ist ein Auszug aus MSDN, aus der hervorgeht, welche "Ngen" ist ein:

>Native Image Generator (*Ngen.exe*) ist ein Tool, das die Leistung von verwalteten Anwendungen verbessert. *Ngen.exe* systemeigene Images, die Dateien mit kompiliertem prozessorspezifischen Computercode und installiert sie in den Cache für systemeigene Images auf dem lokalen Computer erstellt. Die Laufzeit kann systemeigene Abbilder aus dem Cache nutzen und muss nicht den JIT (Just-In-Time)-Compiler verwenden, um die ursprüngliche Assembly zu kompilieren.
>
>von [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Damit auf "Ngen", eine Assembly muss die VSIX-Datei installiert sein "pro pro-Computer-Instanz". Dies kann aktiviert werden, indem Sie das Kontrollkästchen "alle Benutzer" Einchecken der `extension.vsixmanifest` Designer:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Gewusst wie: Aktivieren von Ngen

Um Ngen für eine Assembly zu aktivieren, können Sie die **Eigenschaften** Fenster in Visual Studio.

Es gibt 4 Eigenschaften, die festgelegt werden können:

1. **NGen** (boolesch): bei "true", Visual Studio-Installer wird "Ngen" die Assembly.
2. **NGen-Anwendung** (Zeichenfolge) – Ngen bietet die Möglichkeit, einer Anwendung nutzen *"App.config"* Datei, um die Assemblyabhängigkeiten aufzulösen. Dieser Wert sollte festgelegt werden zu einer Anwendung, deren *"App.config"* (in Bezug auf das Visual Studio-Installationsverzeichnis) verwenden möchten.
3. **NGen-Architektur** (Enum) – die Architektur Ihrer Assembly nativ kompilieren. Die Optionen sind: ein. B für "NotSpecified". X86 c. X64 d. Alle
4. **NGen-Priorität** (ganze Zahl zwischen 1 und 3): die Ngen-Prioritätsebene finden Sie unter [Ngen.exe Prioritätsstufen](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Hier wird erläutert, die **Eigenschaften** Fenster in Aktion:

![NGen in Eigenschaften](media/ngen-in-properties.png)

Dadurch wird die Metadaten hinzugefügt, um den Projektverweis innerhalb des VSIX-Projekts *csproj* Datei:

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

Der Designer Änderung der Eigenschaft gelten für mehr als nur-Projekt-verweisen. Sie können die Ngen-Metadaten für Elemente festlegen, in Ihr Projekt (mit der gleichen oben beschriebenen Methoden) so lange, wie die Elemente .NET Assemblys sind.