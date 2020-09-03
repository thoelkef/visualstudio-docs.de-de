---
title: Entfernen von Quell Code Verwaltungsinformationen aus. Proj und. SLN-Dateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199377"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Entfernen von Informationen der Quellcodeverwaltung aus PROJ- und SLN-Dateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In Version 1,2 der Quellcodeverwaltungs-Plug-in-API werden SCC-Informationen in einem Mssccprj gespeichert. SCC-Datei. Der Vorteil von Mssccprj. SCC File ist, dass die SCC-Informationen nicht Quell gesteuert werden, wie Sie sich in proj-und SLN-Dateien befinden.  
  
## <a name="version-12-changes"></a>Änderungen der Version 1,2  
 In Quellcodeverwaltungs-Plug-ins, die auf der API-Version 1,1 der Quellcodeverwaltungs-Plug-in basieren, werden Informationen zur Quell Code Verwaltung in den Projektdateien (. proj) und in Projektmappendateien (. sln) gespeichert. Der Speicherort der Quell Code Verwaltung wird durch den Pfad für die Quell Code Verwaltung festgelegt, und der angegebene Speicherort in der Datenbank wird von ProjName angegeben. Dieses Verhalten kann Probleme nach Verzweigungen, Verzweigungen oder Kopier Vorgängen verursachen, da der Proxy Name in der Regel nach einer dieser Vorgänge ungültig wäre.  
  
 In der Quellcodeverwaltungs-Plug-in-API-Version 1,1 hat die IDE ~ Sak-Dateien verwendet, um zu erkennen, ob ein Plug-in Mssccprj unterstützt. SCC-Methode zum Speichern von Informationen zur Quell Code Verwaltung. Die API-Version 1,2 der Quellcodeverwaltungs-Plug-in bietet eine neue Funktion zum Erkennen der Unterstützung für Mssccprj. SCC-Datei ohne Verwendung einer ~ Sak-Datei. Weitere Informationen finden Sie unter [eliminieren von ~ Sak-Dateien](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
