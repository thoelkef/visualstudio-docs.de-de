---
title: Entfernen von Informationen über die Quelle aus. Proj und. Sln-Dateien | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 695a4ccfc5da20bda25c78929488625c244959a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128986"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Entfernen von Informationen über die Quelle aus. Proj und. Sln-Dateien
In Version 1.2 von der Quelle Steuerelement-Plug-in-API SCC werden Informationen in einem MSSCCPRJ gespeichert. SCC-Datei. Der Vorteil der MSSCCPRJ. SCC-Datei ist, dass die SCC-Informationen ist nicht im Quellmodell - gesteuert, wie es in ".proj" und die SLN-Dateien ist.  
  
## <a name="version-12-changes"></a>Versionsänderungen 1.2  
 Informationen zur Versionskontrolle wird im Datenquellen-Steuerelement-Plug-ins, die abhängig von der Quelle Steuerelement-Plug-in-API Version 1.1, im Projekt (".proj") und Projektmappendateien (.sln) gespeichert. Der Speicherort der Informationen über die Quelle für die Datenbank wird durch die AuxPath angegeben, und die Position innerhalb der Datenbank vom ProjName angegeben ist. Dieses Verhalten kann nach Branch, "Verzweigung" oder Kopiervorgänge Probleme verursachen, da der Projektname in der Regel nach jedem dieser Vorgänge werden.  
  
 In der Quelle Steuerelement-Plug-in-API Version 1.1, die IDE verwendet ~ SAK Dateien zu erkennen, ob ein plug-in die MSSCCPRJ unterstützt. SCC-Methode zum Speichern von Informationen über die Quelle. Die Datenquellen-Steuerelement-Plug-in-API Version 1.2 bietet eine neue Funktion für die Unterstützung für MSSCCPRJ erkennen. SCC-Datei ohne Verwendung einer ~ SAK-Datei. Weitere Informationen finden Sie unter [wegfallen ~ SAK Dateien](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)