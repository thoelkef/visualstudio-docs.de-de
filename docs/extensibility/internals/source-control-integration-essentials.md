---
title: Source Control Integration Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705238"
---
# <a name="source-control-integration-essentials"></a>Grundlagen der Integration der Quellcodeverwaltung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt zwei Arten der Quellcodeverwaltungsintegration: ein Quellcodeverwaltungs-Plug-In, das grundlegende Funktionen bereitstellt und mithilfe der Quellcodeverwaltungs-Plug-In-API (früher als MSSCCI-API bekannt) erstellt wird, und eine VSPackage-basierte Quellcodeverwaltungsintegrationslösung, die robustere Funktionen bereitstellt.

## <a name="source-control-plug-in"></a>Quellcodeverwaltung Plug-in
 Ein Quellcodeverwaltungs-Plug-In wird als DLL geschrieben, die die Quellcodeverwaltungs-Plug-In-API implementiert. Die Registrierungs- und Quellcodeverwaltungsintegrationsfunktionalität wird über die API bereitgestellt. Dieser Ansatz ist einfacher zu implementieren als ein Quellcodeverwaltungs-VSPackage und verwendet die Benutzeroberfläche (UI) für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] meisten Quellcodeverwaltungsvorgänge.

 Gehen Sie folgendzubearid vor, um ein Quellcodeverwaltungs-Plug-In mithilfe der Quellcodeverwaltungs-Plug-In-API zu implementieren:

1. Erstellen Sie eine DLL, die die in [Denksteuerungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)angegebenen Funktionen implementiert.

2. Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge erstellen, wie unter [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)beschrieben.

3. Erstellen Sie eine Hilfsbenutzeroberfläche, und zeigen Sie sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] an, wenn Sie vom Quellcodeverwaltungsadapterpaket (der Komponente, die die Quellcodeverwaltungsfunktionalität über Quellcodeverwaltungs-Plug-Ins verarbeitet) aufgefordert werden.

   Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Quellcodeverwaltung VSPackage
 Mit einer Quellcodeverwaltungs-VSPackage-Implementierung können Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einen benutzerdefinierten Ersatz für die Quellcodeverwaltungsbenutzeroberfläche entwickeln. Dieser Ansatz bietet vollständige Kontrolle über die Quellcodeverwaltungsintegration, erfordert jedoch die Bereitstellung der UI-Elemente und die Implementierung der Quellcodeverwaltungsschnittstellen, die andernfalls im Rahmen des Plug-In-Ansatzes bereitgestellt würden.

 Um ein Quellcodeverwaltungs-VSPackage zu implementieren, müssen Sie:

1. Erstellen und registrieren Sie Ihr eigenes Quellcodeverwaltungs-VSPackage, wie unter [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)beschrieben.

2. Ersetzen Sie die standardmäßige Quellcodeverwaltungsbenutzeroberfläche durch Ihre benutzerdefinierte Benutzeroberfläche. Siehe [Benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Geben Sie die zu verwendenden Glyphen an, und behandeln Sie die Symbolereignisse **des Projektmappen-Explorers.** Siehe [Glyphensteuerung](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Behandeln Sie Abfragebearbeitungs- und Abfragespeichern-Ereignisse, wie in [Query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)gezeigt.

   Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht](../../extensibility/internals/source-control-integration-overview.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
