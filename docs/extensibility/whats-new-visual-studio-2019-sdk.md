---
title: Neues in Visual Studio SDK 2019 | Microsoft-Dokumentation
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f818d89a51603bf2698e6c1db034f5341f23098
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086560"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Neuigkeiten im Visual Studio 2019 SDK

Visual Studio SDK hat die folgenden neuen und aktualisierten Funktionen für Visual Studio-2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Synchron automatisch geladen Erweiterungen Warnung

Benutzer sehen jetzt eine Warnung, wenn ihre installierten Erweiterungen synchron automatisch geladen, beim Start sind. Erfahren Sie mehr über die Warnung am [synchron automatisch geladen Erweiterungen](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Zentrale, einheitliche Visual Studio SDK

Sie erhalten nun alle Visual Studio SDK-Ressourcen über ein einzelnes NuGet-Paket [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Registrierung der Editor-Erweiterungen

Seit seiner Erstellung unterstützt Visual Studio-Editor für benutzerdefinierte Registrierung, in dem ein Editor kann die Affinität für bestimmte Erweiterungen (beispielsweise "XAML" und "rc"), oder deklarieren, die sie eignet sich für eine beliebige Erweiterung (. *). Ab Visual Studio 2019 Version 16.1, und erweitern wir die Unterstützung für die Editor-Registrierung.

### <a name="filenames"></a>Dateinamen

Zusätzlich zur oder anstelle Registrieren der Unterstützung für eine bestimmte Dateierweiterung, ein Editor kann zu registrieren, dass sie bestimmte Dateinamen unterstützt, durch Anwenden der neuen `ProvideEditorFilename` -Attribut auf die Anmerkung der Redaktion-Paket.

Beispielsweise, ein Editor, alle JSON-Dateien unterstützt, würde gelten diese `ProvideEditorExtension` -Attribut auf das Paket:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Ab 16.1, wenn MyEditor nur ein paar bekannte JSON-Dateien unterstützt, sie können stattdessen gelten diese `ProvideEditorFilename` Attribute des Pakets:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Ein Editor kann eine oder mehrere UIContexts registrieren, die darstellen, wenn es aktiviert ist. UIContexts werden registriert, indem Sie eine oder mehrere Instanzen der Anwendung `ProvideEditorUIContextAttribute` zum Paket, das den Editor registriert.

Wenn ein Editor registrierte UIContexts aufweist:

- Wenn mindestens eines der registrierten UIContexts aktiv ist, wenn eine Datei mit der angegebenen Erweiterung geöffnet wird, ist der Editor in der Editor für Suche enthalten.
- Wenn keines der registrierten UIContexts aktiv ist, wird der Editor ist nicht in der Editor für Suche enthalten.

Wenn ein Editor UIContexts registrieren nicht, ist es immer in der Editor für Suche für diese Erweiterung enthalten.

Wenn Sie ein Editor ist nur verfügbar Wenn z. B. eine C# Projekt geöffnet ist, sie können diese Affinität deklarieren, indem Sie anwenden ein `ProvideEditorUIContext` Attribut:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```