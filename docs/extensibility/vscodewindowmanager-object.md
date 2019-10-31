---
title: Vscoabwindowmanager-Objekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c67fb719c6ec87e7707a406e2e7f67cd71569b39
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189032"
---
# <a name="vscodewindowmanager-object"></a>Vscoabwindowmanager-Objekt

Der Sprachdienst implementiert den Code Fenster-Manager und ist für die Verwaltung von Zusatzelementen zuständig (z. b. die Dropdown Leiste). Weitere Informationen finden Sie unter [Anpassen von Code Fenstern mit der Legacy-API](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

In der folgenden Tabelle werden die Schnittstellen im `VSCodeWindowManager` Objekt angezeigt.

|Interface|Beschreibung|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Ermöglicht das Hinzufügen oder Entfernen von Zusatzelemente (z. b. Dropdown leisten) zu einem Code Fenster.|