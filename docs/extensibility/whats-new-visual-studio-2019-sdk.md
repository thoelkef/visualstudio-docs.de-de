---
title: Neuerungen im Visual Studio 2019 SDK | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740398"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Neuigkeiten im Visual Studio 2019 SDK

Das Visual Studio SDK verfügt über die folgenden neuen und aktualisierten Features für Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Synchrone Warnung für automatisch geladene Erweiterungen

Benutzer erhalten nun eine Warnung, wenn eine ihrer installierten Erweiterungen beim Start synchron automatisch geladen wird. Weitere Informationen zu der Warnung finden Sie unter [Synchronly autoloaded extensions](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Einzelnes, einheitliches Visual Studio SDK

Sie können jetzt alle Visual Studio SDK-Assets über ein einzelnes NuGet-Paket [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk)abrufen.

## <a name="editor-registration-enhancements"></a>Verbesserungen bei der Editorregistrierung

Seit seiner Erstellung hat Visual Studio die benutzerdefinierte Editorregistrierung unterstützt, bei der ein Editor seine Affinität für bestimmte Erweiterungen (z. B. .xaml und .rc) deklarieren kann oder dass er für jede Erweiterung (.*) geeignet ist. Ab Visual Studio 2019 Version 16.1 erweitern wir die Unterstützung für die Editor-Registrierung.

### <a name="filenames"></a>Dateinamen

Zusätzlich zu oder anstelle der Registrierung von Unterstützung für eine bestimmte Dateierweiterung kann ein Editor `ProvideEditorFilename` registrieren, dass er bestimmte Dateinamen unterstützt, indem er das neue Attribut auf das Paket des Editors anwendet.

Beispielsweise würde ein Editor, der alle JSon-Dateien unterstützt, dieses `ProvideEditorExtension` Attribut auf sein Paket anwenden:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Ab 16.1 kann MyEditor, wenn MyEditor nur einige bekannte JSon-Dateien `ProvideEditorFilename` unterstützt, stattdessen diese Attribute auf sein Paket anwenden:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Ein Editor kann einen oder mehrere UIContexts registrieren, die darstellen, wann er aktiviert ist. UIContexts werden registriert, indem eine `ProvideEditorUIContextAttribute` oder mehrere Instanzen von auf das Paket angewendet werden, das den Editor registriert.

Wenn ein Editor UIContexts registriert hat:

- Wenn mindestens einer der registrierten UIContexts aktiv ist, wenn eine Datei mit der angegebenen Erweiterung geöffnet wird, wird der Editor in die Editorsuche einbezogen.
- Wenn keiner der registrierten UIContexts aktiv ist, wird der Editor nicht in die Editorsuche einbezogen.

Wenn ein Editor keine UIContexts registriert, wird er immer in der Editorsuche nach dieser Erweiterung berücksichtigt.

Wenn z. B. ein Editor nur verfügbar ist, wenn ein C-Projekt `ProvideEditorUIContext` geöffnet ist, kann er diese Affinität deklarieren, indem er ein Attribut anwendet:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
