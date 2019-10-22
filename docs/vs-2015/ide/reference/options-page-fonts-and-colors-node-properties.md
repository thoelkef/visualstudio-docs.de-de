---
title: Optionsseite, Eigenschaften des Knotens „Schriftarten und Farben“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662425"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Optionsseite, Eigenschaften des Knotens "Schriftarten und Farben"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dieses Dokument beschreibt die Eigenschaften der Schriftarten und Farben für ein Toolfenster, das unter **Schriftarten und Farben** in der Kategorie **Umgebung** des Dialogfelds **Optionen** registriert ist. Dadurch wird die Dynamik von Gruppen von einfärbbaren Elementen unterstützt, die sich ändern kann, wenn VSPackages installiert oder deinstalliert werden.

 Im folgenden Bereich wird ein Beispiel für einen registrierten Fenstertyp und die für jedes Fenster verfügbaren Eigenschaften besprochen.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Text-Editor oder Drucker oder Dialogfelder oder Toolfenster
 `DTE.Properties("FontsAndColors", "TextEditor")`

 -oder-

 `DTE.Properties("FontsAndColors", "Printer")`

 Oder

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Eigenschaftenelementname|Wert|BESCHREIBUNG|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (Zeichenfolge)|Der zu verwendende Name einer Schriftart, z.B. „Courier New.“|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Ein <xref:EnvDTE.vsFontCharSet>-Wert, der den Typ des zu verwendenden Zeichensatzes angibt, z.B. Hebräisch oder Russisch.|
|FontSize|Get/Set (kurzer Name)|Die zu verwendende Schriftgröße in Punkten. Beispielsweise 10 oder 12.|

## <a name="see-also"></a>Siehe auch
 [Steuern von Options Einstellungen](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [Festlegen der Namen von Eigenschaften Elementen auf Options Seiten](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [Optionen Seite, Umgebungs Knoten Eigenschaften](../../ide/reference/options-page-environment-node-properties.md) [Optionen Seite, Eigenschaften des Knotens "Text-Editor](../../ide/reference/options-page-text-editor-node-properties.md) "
