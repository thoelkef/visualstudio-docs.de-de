---
title: VSCodeWindowManager-Objekt | Microsoft Docs
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
ms.openlocfilehash: 17bc9462af55ec9621654bd39cd65a2091f3f73f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740416"
---
# <a name="vscodewindowmanager-object"></a>VSCodeWindowManager-Objekt

Der Sprachdienst implementiert den Codefenster-Manager und ist für die Verwaltung von Verzierungen (z. B. die Dropdown-Leiste) verantwortlich. Weitere Informationen finden Sie unter [Anpassen von Code Windows mithilfe der Legacy-API](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

Die folgende Tabelle zeigt die `VSCodeWindowManager` Schnittstellen im Objekt.

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Ermöglicht das Anlegen von Verzierungen (z. B. Dropdown-Leisten), die einem Codefenster hinzugefügt oder daraus entfernt werden.|
