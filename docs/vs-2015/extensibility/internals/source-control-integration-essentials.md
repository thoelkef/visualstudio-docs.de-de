---
title: Grundlagen der Integration der Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ecd87dfc4c2993023d0c882ce581280204f99d6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232354"
---
# <a name="source-control-integration-essentials"></a>Grundlagen der Integration der Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützt zwei Arten der Integration der quellcodeverwaltung: ein Quellcodeverwaltungs-Plug-Ins, die stellt grundlegende Funktionalität bereit und wird mithilfe der Quell-Plug-in-API (ehemals die MSSCCI-API) und eine VSPackage-basierten Datenquellen-Steuerelement-integrationslösung erstellt, Stellt robuster Funktionen bereit.  
  
## <a name="source-control-plug-in"></a>Quellcodeverwaltung-Plug-in  
 Ein Datenquellen-Steuerelement-Plug-in wird als DLL geschrieben, die die Source-Plug-in-API implementiert. Registrierung und Datenquellen-Steuerelement-Integration-Funktionalität wird über die API bereitgestellt. Dieser Ansatz ist einfacher zu implementieren als ein Quellcodeverwaltungs-VSPackage und verwendet die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Benutzeroberfläche (UI) für die meisten Quellcodeverwaltungsvorgänge.  
  
 Gehen Sie folgendermaßen vor, um ein Quellcodeverwaltungs-Plug-in mit der Source-Plug-in-API zu implementieren:  
  
1.  Erstellen Sie eine DLL, die die angegebenen Funktionen implementiert [Quellcodeverwaltung-Plug-ins](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge, machen, wie in beschrieben [Vorgehensweise: eine Source-Control-Plug-in installieren](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Erstellen Sie eine Hilfsprogramm-UI und Aufforderung durch den Adapter Quellcodeverwaltungspaket anzeigen (die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Komponente, die Quellcodeverwaltungsfunktionen über den Quellcodeverwaltungs-Plug-ins behandelt).  
  
 Weitere Informationen finden Sie unter [ein Datenquellen-Steuerelement-Plug-in erstellen](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Quellcodeverwaltungs-VSPackage  
 Ein Quellcodeverwaltungs-VSPackage-Implementierung können Sie zum Entwickeln von benutzerdefinierten Ersatz für die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Datenquellen-Steuerelement-Benutzeroberfläche. Dieser Ansatz bietet vollständige Kontrolle über die Integration der quellcodeverwaltung, aber es erfordert, dass Sie die Elemente der Benutzeroberfläche bereitstellen und implementieren Sie die Steuerelement-Schnittstellen, die unter der-Plug-in-Ansatz bereitgestellt werden. Andernfalls würde.  
  
 Um ein Quellcodeverwaltungs-VSPackage implementieren zu können, müssen Sie folgende Aktionen ausführen:  
  
1.  Erstellen und registrieren Sie Ihrer eigenen quellcodeverwaltung VSPackage, siehe [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Ersetzen Sie die Standard-quellcodeverwaltung Benutzeroberfläche, durch die benutzerdefinierte Benutzeroberfläche. Finden Sie unter [benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Geben Sie die Symbole verwendet werden, und das behandeln **Projektmappen-Explorer** Symbol-Ereignisse. Finden Sie unter [Glyphensteuerung](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Abfrage bearbeiten und speichern Sie die Abfrage Ereignisse behandeln, siehe [Abfrage bearbeiten die Abfrage speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht](../../extensibility/internals/source-control-integration-overview.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

