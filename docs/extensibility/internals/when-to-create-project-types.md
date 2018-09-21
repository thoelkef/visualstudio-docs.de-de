---
title: Gründe für das Erstellen von Projekttypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5bfa51dfbed4fb0c78892b06e9377e36a1be38ea
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495218"
---
# <a name="when-to-create-project-types"></a>Gründe für das Erstellen von Projekttypen
Erstellen einen neuen Projekttyp bildet die Grundlage für Anpassung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für Ihre Benutzer. Erstellen einen neuen Projekttyp ist jedoch nicht erforderlich, damit alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anpassungen. Die folgenden Richtlinien sollten leichter bestimmen, ob ein neuer Projekttyp für Ihr Szenario erforderlich ist.  
  
## <a name="create-a-new-project-type"></a>Erstellen Sie einen neuen Projekttyp  
 Sie müssen einen Projekttyp erstellen, wenn Sie anpassen möchten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , die in eine oder mehrere der folgenden Methoden verwendet:  
  
-   Teilnahme an Build, bereitstellen, Konfigurationen und Datenquellen-Steuerelement.  
  
-   Bieten Sie Unterstützung für Remotedebuggen.  
  
-   Anzeigen der Projektelemente im **Projektmappen-Explorer**.  
  
-   Verwenden der **geöffneten Projekt** oder **neues Projekt** Dialogfeld.  
  
-   Schachtelung von Projekt zu unterstützen.  
  
## <a name="extend-an-existing-project-type"></a>Erweitern Sie einen vorhandenen Projekttyp  
 Möglicherweise möchten Sie einen neuen Projekttyp zu erstellen, können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auf folgende Weise ändern oder erweitern das Verhalten eines vorhandenen Projekts-Typs, z. B. die Änderung des Buildprozesses für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte:  
  
-   Arbeiten Sie mit mehreren Dateien als einzelne Einheit ein.  
  
-   Eine einzelne Datei als Hierarchie von untergeordneten Elementen anzeigen.  
  
-   Zeigen Sie einen Befehlskontext um Editoren.  
  
-   Zeigen Sie einen Dienstkontext für Editoren an.  
  
## <a name="use-an-existing-project-type"></a>Verwenden Sie einen vorhandenen Projekttyp  
 Erstellen eines neuen Projekts ist manchmal nicht erforderlich. Die folgende Tabelle zeigt die Aufgaben, denen Sie nicht, erstellen Sie einen Projekttyp für verfügen.  
  
|Aufgabe|Beschreibung|  
|----------|-----------------|  
|Behandeln von Kommentaren|Jedem VSPackage kann Befehle verarbeiten.|  
|Erstellen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument Windows und Editoren](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|  
|Besitzer von windows|Sie können sowohl Tool-und Dokumentfenster erstellen, ohne dass einen neuer Projekttyp hinzugefügt.|  
|Verfügbarmachen von Eigenschaften im Eigenschaftenfenster|Alle Objekte können Eigenschaften verfügbar machen.|  
  
## <a name="create-a-project-subtype"></a>Erstellen von einem Projektuntertyp  
 Sie können die Projektuntertypen verwenden, um ein verwaltetes Projekt zu erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projektuntertypen com-Aggregation verwenden Sie zum Erweitern von verwalteter Projekten, die bei Microsoft geschrieben [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Mit COM-Aggregation können ein Großteil der systemimplementierung verwaltetes Projekt wiederverwenden und dennoch für ein bestimmtes Szenario durch die Aggregation und die Verwendung von unterstützende Schnittstellen anpassen. Weitere Informationen zu Projektuntertypen, finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dokument Windows und Editoren](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)