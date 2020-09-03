---
title: Bestimmen, ob ein Quellcodeverwaltungs-VSPackage implementiert werden soll | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196797"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Bestimmen, ob ein Quellcodeverwaltungs-VSPackage implementiert werden sollte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Abschnitt werden die Optionen der Quellcodeverwaltungs-Plug-ins und der Quellcodeverwaltungs-VSPackages zur Erweiterung der Quell Code Verwaltungslösungen erläutert, und es werden umfassende Richtlinien zur Auswahl eines geeigneten Integrations Pfads  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Lösung für kleine Quell Code Verwaltung mit eingeschränkten Ressourcen  
 Wenn Sie nur über begrenzte Ressourcen verfügen und nicht mit dem Aufwand zum Schreiben eines Quell Code Verwaltungs Pakets belastet werden können, können Sie API-basierte Plug-Ins für die Quellcodeverwaltungs-Plug-ins erstellen. Dies ermöglicht es Ihnen, nebeneinander mit Quell Code Verwaltungs Paketen zu arbeiten, und Sie können bei Bedarf zwischen den Quellcodeverwaltungs-Plug-ins und-Paketen wechseln. Weitere Informationen finden Sie unter [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Lösung für große Quell Code Verwaltung mit umfangreichem Featuresatz  
 Wenn Sie eine Quell Code Verwaltungs Lösung implementieren möchten, die ein umfangreiches Quell Code Verwaltungsmodell bereitstellt, das nicht mit der Quellcodeverwaltungs-Plug-in-API ordnungsgemäß erfasst wird, können Sie ein Quell Code Verwaltungspaket als Integrations Pfad in Erwägung ziehen. Dies trifft vor allem dann zu, wenn Sie stattdessen das Quell Code Verwaltungs Adapter-Paket ersetzen (das mit Quellcodeverwaltungs-Plug-ins kommuniziert und eine einfache Benutzeroberfläche für die Quell Code Verwaltung bereitstellt), sodass Sie die Quell Code Verwaltungs Ereignisse auf benutzerdefinierte Weise behandeln können. Wenn Sie bereits über eine zufriedenstellende Quell Code Verwaltungs Benutzeroberfläche verfügen und diese Funktion in beibehalten möchten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , können Sie mit der Option "Quell Code Verwaltungspaket" genau das tun. Das Quell Code Verwaltungspaket ist nicht generisch und ausschließlich für die Verwendung mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE vorgesehen.  
  
 Wenn Sie eine Lösung für die Quell Code Verwaltung implementieren möchten, die Flexibilität und eine umfassendere Kontrolle über die Quell Code Verwaltungs Logik und die Benutzeroberfläche bietet, bevorzugen Sie möglicherweise die Integrations Route für das Quell Code Verwaltungspaket. Sie können:  
  
1. Registrieren Sie Ihr eigenes VSPackage für die Quell Code Verwaltung (siehe [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Ersetzen Sie die Standardbenutzer Oberfläche der Quell Code Verwaltung durch Ihre benutzerdefinierte Benutzeroberfläche (siehe Benutzer [definierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Geben Sie Symbole an, die verwendet werden sollen, und behandeln Sie Projektmappen-Explorer Glyphe-Ereignisse (siehe [Glyphe-Steuer](../../extensibility/internals/glyph-control-source-control-vspackage.md)Element).  
  
4. Behandeln von Ereignissen zum Bearbeiten und Abfragen von Abfragen (siehe Speichern der Abfrage [Bearbeiten](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
