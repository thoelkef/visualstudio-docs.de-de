---
title: Ngen-Support in VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702398"
---
# <a name="ngen-support-in-vsix-v3"></a>NGen-Unterstützung in VSIX v3

Mit Visual Studio 2017 und dem neuen VSIX v3 (Version 3) Erweiterungsmanifestformat können Erweiterungsentwickler ihre Assemblys jetzt bei der Installation "ngenen".

Im Folgenden finden Sie einen Auszug aus MSDN, der erklärt, was "ngen" tut:

>Der Native Image Generator (*Ngen.exe*) ist ein Tool, das die Leistung von verwalteten Anwendungen verbessert. *Ngen.exe* erstellt systemeigene Images, bei denen es sich um Dateien mit kompiliertem prozessorspezifischen Computercode handelt, und installiert sie im systemeigenen Image-Cache auf dem lokalen Computer. Die Laufzeit kann systemeigene Abbilder aus dem Cache nutzen und muss nicht den JIT (Just-In-Time)-Compiler verwenden, um die ursprüngliche Assembly zu kompilieren.
>
>von [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Um eine Baugruppe zu "ngenen", muss der VSIX "pro Instanz pro Maschine" installiert werden. Dies kann aktiviert werden, indem Sie das `extension.vsixmanifest` Kontrollkästchen "Alle-Benutzer" im Designer aktivieren:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>So aktivieren Sie Ngen

Um ngen für eine Assembly zu aktivieren, können Sie das **Eigenschaftenfenster** in Visual Studio verwenden.

Es gibt 4 Eigenschaften, die festgelegt werden können:

1. **Ngen** (Boolean) - Wenn true, "ngen" das Visual Studio-Installationsprogramm die Assembly.
2. **Ngen-Anwendung** (Zeichenfolge) - Ngen bietet die Möglichkeit, die *App.config-Datei* einer Anwendung zu verwenden, um Assemblyabhängigkeiten aufzulösen. Dieser Wert sollte auf eine Anwendung festgelegt werden, deren *app.config* Sie verwenden möchten (relativ zum Visual Studio-Installationsverzeichnis).
3. **Ngen Architecture** (enum) - Die Architektur zum nativkompilieren Sie Ihre Assembly. Die Optionen sind: a. Nicht spezifiziert b. X86 c. X64 d. Alle
4. **Ngen-Priorität** (ganzzahlig zwischen 1 und 3) - Die Ngen-Prioritätsstufe ist auf [Ngen.exe-Prioritätsstufen](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)dokumentiert.

Hier ist ein Blick auf das **Eigenschaftenfenster** in Aktion:

![ngen in Eigenschaften](media/ngen-in-properties.png)

Dadurch werden Metadaten zum Projektverweis in der *.csproj-Datei* des VSIX-Projekts hinzugefügt:

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

> [!NOTE]
> Sie können die .csproj-Datei direkt bearbeiten, wenn Sie es vorziehen.

## <a name="extra-information"></a>Zusätzliche Informationen

Die Eigenschaftendesigneränderungen gelten für mehr als nur Projektverweise. Sie können die Ngen-Metadaten auch für Elemente innerhalb des Projekts festlegen (mit den oben beschriebenen Methoden), solange es sich bei den Elementen um .NET-Assemblys handelt.
