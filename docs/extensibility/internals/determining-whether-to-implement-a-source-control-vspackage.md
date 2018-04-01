---
title: Bestimmen, ob eine Datenquellen-Steuerelement VSPackage implementiert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 88281496c2e8350f910feda7934e2b55a494243b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Bestimmen, ob eine Datenquellen-Steuerelement VSPackage implementieren
In diesem Abschnitt werden die Optionen des Datenquellen-Steuerelement-Plug-ins und quellcodeverwaltung VSPackages zum Erweitern der quellcodeverwaltung Projektmappen und bietet umfassende Richtlinien zum Auswählen eines geeigneten Integration Pfads näher erläutert.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Kleine Source Control-Lösung mit eingeschränkten Ressourcen  
 Wenn Sie nur Ressourcen begrenzte über und können nicht mit den Aufwand für das Schreiben von einem Steuerelement Quellpaket belastet werden, können Sie die Datenquellen-Steuerelement-Plug-in-API-basierte-Plug-ins erstellen. Dies ermöglicht Ihnen, parallel Quellpakete-Steuerelements zu arbeiten, und Sie können zwischen Source Control-Plug-ins und -Paketen nach Bedarf wechseln. Weitere Informationen finden Sie unter [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Große Source Control-Lösung mit einem Satz von Rich-Funktion  
 Wenn eine Source Control-Lösung zu implementieren, die eine umfangreiche Steuerelement Quellmodell, die bereitstellt mithilfe der Datenquellen-Steuerelement-Plug-in-API nicht adäquat erfasst werden sollen, könnten Sie ein Steuerelement Source-Paket als Pfad der Integration. Dies gilt besonders, wenn stattdessen das Adapter Quellcodeverwaltungspaket ersetzen würde (der kommuniziert mit Source Control-Plug-ins und bietet eine grundlegende quellcodeverwaltung UI) mit Ihren eigenen, damit Sie die Quelle Steuerelementereignisse auf benutzerdefinierte Weise behandeln können. Falls Sie noch eine zufriedenstellende Quelle UI steuern und diesen Erfahrungen in beibehalten möchten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], den Quellcodeverwaltungs-Paket-Option können Sie nur diese Aufgaben ausführen. Das Quellcodeverwaltungspaket ist nicht generisch und dient ausschließlich zur Verwendung mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Wenn Sie möchten eine Source Control-Lösung zu implementieren, die Flexibilität und umfangreichere Steuerung der Quelle steuernder Logik und die Benutzeroberfläche bereitstellt, empfiehlt die Datenquellen-Steuerelement Paket Integration Route. Sie haben folgende Möglichkeiten:  
  
1.  Registrieren Ihrer eigenen quellcodeverwaltung VSPackage (finden Sie unter [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Ersetzen Sie die Standard-Datenquellen-Steuerelements UI durch die benutzerdefinierte Benutzeroberfläche (siehe [benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Angeben von Glyphen verwendet werden, und Behandeln von Ereignissen der Projektmappen-Explorer-Symbol (finden Sie unter [Glyphe Steuerelement](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Abfrage bearbeiten und speichern Sie die Abfrage Ereignisse zu behandeln (finden Sie unter [Abfrage bearbeiten die Abfrage speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)