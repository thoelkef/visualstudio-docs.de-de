---
title: Source Control Integration Essentials | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c3e93eb86fdc252f162331033207db5bdaa1569
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-integration-essentials"></a>Source Control Integration Essentials
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Arten der Integration der quellcodeverwaltung: ein Quellcodeverwaltungs-Plug-Ins, die grundlegende Funktionalität bereitstellt und basiert auf der Quelle-Plug-in-API mit dem (früher als MSSCCI-API) und eine VSPackage-basierten Datenquellen-Steuerelement-integrationslösung, Stellt eine robustere Funktionalität bereit.  
  
## <a name="source-control-plug-in"></a>Datenquellen-Steuerelement-Plug-in  
 Ein Datenquellen-Steuerelement-Plug-in wird als DLL geschrieben, die die Quelle Steuerelement-Plug-in-API implementiert. Registrierung und Datenquellen-Steuerelement-Integrationsfunktionalität wird über die API bereitgestellt. Dieser Ansatz ist einfacher zu implementieren als ein Datenquellen-Steuerelement VSPackage und verwendet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Benutzeroberfläche (UI) für die meisten Quellcodeverwaltungsvorgänge.  
  
 Gehen Sie folgendermaßen vor, um ein Quellcodeverwaltungs-Plug-in mithilfe der Datenquellen-Steuerelement-Plug-in-API zu implementieren:  
  
1.  Erstellen Sie eine DLL, die die angegebenen Funktionen implementiert [Quellcodeverwaltung-Plug-ins](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge machen, wie in beschrieben [Vorgehensweise: Installieren Sie eine Datenquellen-Steuerelement-Plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Erstellen Sie eine UI-Hilfsprogramm und zeigen Sie sie nach Aufforderung durch das Quellcodeverwaltungspaket-Adapter (der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponente, Quellcodeverwaltungsfunktion über Datenquellen-Steuerelement-Plug-ins verarbeitet).  
  
 Weitere Informationen finden Sie unter [ein Datenquellen-Steuerelement-Plug-in erstellen](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Source Control VSPackage  
 Ein VSPackage-Implementierung des Datenquellen-Steuerelement können Sie zum Entwickeln von benutzerdefinierten Ersatz für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quellcodeverwaltung UI. Dieser Ansatz bietet vollständige Kontrolle über die Integration der quellcodeverwaltung, aber es sind die Elemente der Benutzeroberfläche und implementieren die Datenquellen-Steuerelement-Schnittstellen, die andernfalls in der Plug-in-Ansatz bereitgestellt wird.  
  
 Um ein Datenquellen-Steuerelement VSPackage implementieren zu können, müssen Sie folgende Aktionen ausführen:  
  
1.  Erstellen und registrieren Sie Ihren eigenen quellcodeverwaltung VSPackage, wie in beschrieben [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Ersetzen Sie das Standardsteuerelement Quelle UI, durch die benutzerdefinierte Benutzeroberfläche. Finden Sie unter [benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Geben Sie Glyphen verwendet werden, und das behandeln **Projektmappen-Explorer** Glyphe Ereignisse. Finden Sie unter [Glyphe Steuerelement](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Abfrage bearbeiten und speichern Sie die Abfrage Ereignisse behandeln, wie gezeigt in [Abfrage bearbeiten die Abfrage speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Weitere Informationen finden Sie unter [Erstellen eines Source Control VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht](../../extensibility/internals/source-control-integration-overview.md)   
 [Erstellen ein Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)