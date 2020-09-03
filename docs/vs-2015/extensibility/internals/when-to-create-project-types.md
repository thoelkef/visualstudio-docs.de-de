---
title: Zeitpunkt der Erstellung von Projekttypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b5bc2bacb53973bd552b983b742e4f9e68fe31b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687698"
---
# <a name="when-to-create-project-types"></a>Gründe für das Erstellen von Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie einen neuen Projekttyp erstellen, finden Sie eine Grundlage für [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die Anpassung für Ihre Benutzer. Es ist jedoch nicht erforderlich, einen neuen Projekttyp für alle Anpassungen zu erstellen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Die folgenden Richtlinien sollen Ihnen dabei helfen zu bestimmen, ob ein neuer Projekttyp für Ihr Szenario erforderlich ist.  
  
## <a name="create-a-new-project-type"></a>Neuen Projekttyp erstellen  
 Sie müssen einen Projekttyp erstellen, wenn Sie eine [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oder mehrere der folgenden Methoden anpassen möchten:  
  
- Nehmen Sie an Build, Bereitstellung, Konfigurationen und Quell Code Verwaltung Teil.  
  
- Bietet Debugunterstützung.  
  
- Zeigen Sie Projekt Elemente in **Projektmappen-Explorer**an.  
  
- Verwenden Sie das Dialogfeld **Projekt öffnen** oder **Neues Projekt** .  
  
- Unterstützung der Projekt Schachtelung  
  
## <a name="extend-an-existing-project-type"></a>Erweitern eines vorhandenen Projekt Typs  
 Möglicherweise möchten Sie einen neuen Projekttyp erstellen, der auf [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die folgenden Arten verwenden kann, um das Verhalten eines vorhandenen Projekt Typs zu ändern oder zu erweitern, z. b. zum Ändern des Buildprozesses für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Projekte:  
  
- Arbeiten Sie mit mehreren Dateien als einzelne Einheit.  
  
- Zeigt eine einzelne Datei als Hierarchie von unter Elementen an.  
  
- Anzeigen eines Befehls Kontexts um Editoren.  
  
- Zeigen Sie einen Dienst Kontext für Editoren an.  
  
## <a name="use-an-existing-project-type"></a>Vorhandenen Projekttyp verwenden  
 Das Erstellen eines neuen Projekts ist manchmal nicht erforderlich. In der folgenden Tabelle sind die Tasks aufgeführt, für die Sie keinen Projekttyp erstellen müssen.  
  
|Aufgabe|BESCHREIBUNG|  
|----------|-----------------|  
|Verarbeiten von Befehlen|Alle VSPackage können Befehle verarbeiten.|  
|Aufbauen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument Fenster und Editoren](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Besitzende Fenster|Sie können sowohl Tool-als auch Dokument Fenster erstellen, ohne einen neuen Projekttyp hinzuzufügen.|  
|Verfügbar machen von Eigenschaften im Eigenschaftenfenster|Alle-Objekte können Eigenschaften verfügbar machen.|  
  
## <a name="create-a-project-subtype"></a>Erstellen eines Projekt unter Typs  
 Mithilfe von Projekt Untertypen können Sie einen verwalteten Projekttyp erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projekt Untertypen verwenden com-Aggregation, um verwaltete Projekte zu erweitern, die in Microsoft oder geschrieben wurden [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Mit com-Aggregation können Sie einen Großteil der Implementierung des verwalteten Projekt Systems wieder verwenden und dennoch für ein bestimmtes Szenario durch Aggregation und die Verwendung von unterstützenden Schnittstellen anpassen. Weitere Informationen zu Projekt Untertypen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dokument Fenster und-Editoren](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
