---
title: "Bestimmen, ob ein Datenquellen-Steuerelement VSPackage implementieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellcode-Verwaltungspaketen zum Quellcode-Verwaltungspaketen"
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Bestimmen, ob ein Datenquellen-Steuerelement VSPackage implementieren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieser Abschnitt arbeitt die Auswahlmöglichkeiten von VSPackages und Quellcodeverwaltung steckverbindungen Quellcodeverwaltung zum Erweitern von Office\-Projektmappen Quellcodeverwaltung aus und gibt die Grundzüge zum Auswählen eines geeigneten Speicherpfad Integrations.  
  
## Kleine Quellcodeverwaltungs\-Projektmappe mit beschränkten Ressourcen  
 Wenn Sie begrenzte Ressourcen verfügen und nicht zum Mehraufwand zum Schreiben eines pakets Quellcodeverwaltung belastet werden können, können Sie API\-basierte Quellcodeverwaltungs\-Plug\-In des Plug\-Ins erstellen.  Dies ermöglicht es Ihnen, mit paketen Quellcodeverwaltung nebeneinander zu arbeiten, und Sie können zwischen Paketen und steckverbindungen Quellcodeverwaltung bei Bedarf wechseln.  Weitere Informationen finden Sie unter [Auswahl und Registrierung](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## Große Quellcodeverwaltungs\-Projektmappe mit einem umfangreichen Funktionsumfang  
 Wenn Sie eine Projektmappe implementieren möchten, die Quellcodeverwaltung ein Fundgrube steuerelementmodell bereitstellt, das nicht angemessen aufgezeichnet wird, indem das Quellcodeverwaltungs\-Plug\-In API verwendet, halten Sie möglicherweise ein Paket Quellcodeverwaltung Integrations für den Pfad.  Dies gilt besonders, wenn Sie nicht das Quellcodeverwaltungs\-Adapter\-Paket \(d steckverbindungen Quellcodeverwaltung befindet und eine grundlegende Quellcodeverwaltung Benutzeroberfläche bereitstellt\) verfügen, können von ersetzen, um die Ereignisse für Quellcodeverwaltung auf eine benutzerdefinierte Weise behandeln können.  Wenn Sie bereits eine zufrieden stellende Quellcodeverwaltung Benutzeroberfläche aufweisen und dies in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]beibehalten möchten, können Sie die Option Quellcodeverwaltung derzeit das Paket auszuführen.  Das Paket ist nicht generisch Quellcodeverwaltung und ist nur für die Verwendung mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE vorgesehen.  
  
 Wenn Sie eine Projektmappe implementieren möchten, die Quellcodeverwaltung Flexibilität und umfangreicheres Kontrolle über die Benutzeroberfläche der Quellcodeverwaltung und Anwendungslogik bereitstellt, können Sie auch die Quellcodeverwaltung Paket integrations route.  Sie haben folgende Möglichkeiten:  
  
1.  Registrieren Sie besitzen \(siehe VSPackage Quellcodeverwaltung [Auswahl und Registrierung](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)\).  
  
2.  Ersetzen Sie die standardmäßigen über die Benutzeroberfläche der Quellcodeverwaltung benutzerdefinierte Benutzeroberfläche \(siehe [Benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)\).  
  
3.  Geben Sie die zu verwendenden Symbole angezeigt, und behandeln Sie Ereignisse Projektmappen\-Explorer\-Symbol \(siehe [Symbol\-Steuerelement](../../extensibility/internals/glyph-control-source-control-vspackage.md)\).  
  
4.  Handle\-Abfragen\-Bearbeitung und Abfragen\-Abwehr Events \(siehe [Bearbeiten der Abfragen speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)\).  
  
## Siehe auch  
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)