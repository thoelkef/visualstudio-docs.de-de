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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9668336c565b4a3be332509d1c960b067a486785
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583631"
---
# <a name="vscodewindowmanager-object"></a>Vscoabwindowmanager-Objekt

Der Sprachdienst implementiert den Code Fenster-Manager und ist für die Verwaltung von Zusatzelementen zuständig (z. b. die Dropdown Leiste). Weitere Informationen finden Sie unter [Anpassen von Code Fenstern mit der Legacy-API](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true).

In der folgenden Tabelle werden die Schnittstellen im- `VSCodeWindowManager` Objekt angezeigt.

|Schnittstelle|Beschreibung|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Ermöglicht das Hinzufügen oder Entfernen von Zusatzelemente (z. b. Dropdown leisten) zu einem Code Fenster.|