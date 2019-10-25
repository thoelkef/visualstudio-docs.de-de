---
title: Integration der Quell Code Verwaltung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcce3d8fdcc1c99c9b91bfebec572033ff3beb1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723468"
---
# <a name="source-control-integration-essentials"></a>Grundlagen der Integration der Quellcodeverwaltung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Arten der Integration der Quell Code Verwaltung: ein Quellcodeverwaltungs-Plug-in, das grundlegende Funktionen bereitstellt und mithilfe der Quellcodeverwaltungs-Plug-in-API (ehemals MSSCCI-API) und einer VSPackage-basierten Quell Code Verwaltungs Lösung erstellt wird. Das bietet robustere Funktionen.

## <a name="source-control-plug-in"></a>Quellcodeverwaltungs-Plug-in
 Ein Quellcodeverwaltungs-Plug-in wird als DLL geschrieben, die die Quellcodeverwaltungs-Plug-in-API implementiert. Die Integrationsfunktionen für die Registrierung und die Quell Code Verwaltung werden über die API bereitgestellt. Dieser Ansatz ist einfacher zu implementieren als ein VSPackage für die Quell Code Verwaltung und verwendet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Benutzeroberfläche (UI) für die meisten Quell Code Verwaltungsvorgänge.

 Gehen Sie folgendermaßen vor, um ein Quellcodeverwaltungs-Plug-in mithilfe der Quellcodeverwaltungs-Plug-in-API zu implementieren:

1. Erstellen Sie eine DLL, die die in [Quellcodeverwaltungs-Plug-ins](../../extensibility/source-control-plug-ins.md)angegebenen Funktionen implementiert.

2. Registrieren Sie die dll, indem Sie die entsprechenden Registrierungseinträge erstellen, wie unter Vorgehens [Weise: Installieren eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)beschrieben.

3. Erstellen Sie eine hilfsprogrammbenutzer Oberfläche, und zeigen Sie diese an, wenn Sie vom Quellcodeverwaltungs-Adapter Paket (der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponente zur Behandlung der Quell Code Verwaltungs Funktionalität über Quellcodeverwaltungs-Plug-ins)

   Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Quellcodeverwaltungs-VSPackage
 Eine VSPackage-Implementierung der Quell Code Verwaltung ermöglicht die Entwicklung eines angepassten Ersatzes für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Quell Code Verwaltungs Benutzeroberfläche. Dieser Ansatz bietet eine umfassende Kontrolle über die Integration der Quell Code Verwaltung, erfordert jedoch die Bereitstellung der Benutzeroberflächen Elemente und die Implementierung der Quell Code Verwaltungs Schnittstellen, die andernfalls unter dem Plug-in-Ansatz bereitgestellt werden.

 Zum Implementieren eines Quellcodeverwaltungs-VSPackage müssen Sie folgende Schritte ausführen:

1. Erstellen und registrieren Sie Ihr eigenes VSPackage für die Quell Code Verwaltung, wie unter [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)beschrieben.

2. Ersetzen Sie die Standard Oberfläche der Quell Code Verwaltung durch Ihre benutzerdefinierte Benutzeroberfläche. Siehe [benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Geben Sie Symbole an, die verwendet werden sollen, und behandeln Sie **Projektmappen-Explorer** Glyphe-Ereignisse. Siehe [Glyphe-Steuer](../../extensibility/internals/glyph-control-source-control-vspackage.md)Element.

4. Behandeln Sie Ereignisse zum Bearbeiten und Abfragen von Abfragen, wie in [Abfrage Bearbeitungs Abfrage speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)gezeigt.

   Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackages](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht](../../extensibility/internals/source-control-integration-overview.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)