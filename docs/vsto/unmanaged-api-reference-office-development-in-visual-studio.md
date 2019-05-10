---
title: Referenz zur nicht verwalteten API (Office-Entwicklung in Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 238ed42d48903d2d0ef26384245cff80785a8ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978236"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referenz zur nicht verwalteten API (Office-Entwicklung in Visual Studio)

Mit 2007 Microsoft Office System, Office-Anwendungen verwenden die [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md) Schnittstelle, die in einem VSTO-Add-in-Ladekomponente aufgerufen wird, der in enthalten ist das [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Diese Komponente wird zum Laden verwalteter VSTO-Add-ins zu unterstützen. Sie können eine eigene VSTO-Add-In-Ladekomponente erstellen, indem Sie diese Schnittstelle implementiert.

> [!NOTE]
> Möchten Sie bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins verfügen, einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.

## <a name="in-this-section"></a>In diesem Abschnitt

[IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md)

Eine COM-Schnittstelle, die Sie implementieren können, um verwaltete VSTO-Add-Ins in Office-Anwendungen zu laden und zu entladen.
