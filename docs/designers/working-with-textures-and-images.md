---
title: Arbeiten mit Texturen und Bildern | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92d133d688ad009dae1b4e518bdd8c749ebc329f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-textures-and-images"></a>Arbeiten mit Texturen und Bildern
Sie können die Bildbearbeitung in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Erstellen und Bearbeiten von Texturen und Bildern verwenden. Die Bildverarbeitung unterstützt aufwändige Textur- und Bildformate, wie solche, die in der Entwicklung von DirectX-Apps zum Einsatz kommen.  
  
> [!NOTE]
>  Die Bildverarbeitung unterstützt keine Bilder mit geringer Farbtiefe, wie Symbole oder Cursor. Zum Erstellen oder Ändern dieses Typs Bilder können Sie den [Image Editor for Icons](/cpp/windows/image-editor-for-icons)verwenden.  
  
## <a name="textures-and-images"></a>Texturen und Bilder  
 Texturen und Bilder sind, grundlegend betrachtet, nur Tabellen von Daten, die dazu dienen, visuelle Details in Apps mit grafischer Benutzeroberfläche bereitzustellen. Die Art von Detail, die von einer Textur oder einem Bild bereitgestellt wird, hängt vom Einsatzzweck ab, aber Farbmuster, Alphawerte (Transparenz), Oberflächennormale und Höhenwerte stellen gängige Beispiele dar. Der wichtigste Unterschied zwischen einer Textur und einem Bild besteht darin, dass eine Textur für die Verwendung in Kombination mit der Darstellung einer Form bestimmt ist – normalerweise einem 3D-Modell –, um ein vollständiges Objekt oder eine Szene darzustellen, während ein Bild normalerweise eine eigenständige Darstellung des Objekts oder der Szene ist.  
  
 Häufig verwendete Texturarten sind z. B.:  
  
 Texturmaps  
 Texturmaps enthalten Farbwerte, die als ein-, zwei- oder dreidimensionale Matrix organisiert sind. Sie werden verwendet, um Farbdetails auf dem betroffenen Objekt bereitzustellen. Farben werden häufig mithilfe der Farbkanäle RGB (Rot, Grün, Blau) codiert und können einen vierten Kanal, Alpha, zur Darstellung der Transparenz beinhalten. Weniger üblich, aber möglich, ist die Codierung von Farben in einem anderen Farbschema oder die Darstellung von anderen Informationen als Alpha im vierten Kanal – etwa der Höhe.  
  
 Normalmaps  
 Normalmaps enthalten Oberflächennormale. Sie werden verwendet, um Beleuchtungsdetails für das betroffene Objekt bereitzustellen. Normale werden üblicherweise codiert, indem die roten, grünen und blauen Farbkomponenten zum Speichern der X-, Y- und Z-Dimensionen für den Vektor verwendet werden. Es gibt jedoch auch andere Codierungen – beispielsweise Codierungen auf der Grundlage von Polkoordinaten.  
  
 Höhenmaps  
 Höhenmaps enthalten Höhenfelddaten. Sie werden verwendet, um einen Typ von geometrischem Detail auf dem betroffenen Objekt – mithilfe von Shadercode zum Berechnen des gewünschten Effekts – oder Datenpunkte für Einsatzzwecke wie die Geländegenerierung bereitzustellen . Höhenwerte werden normalerweise durch Nutzung eines Kanals in einer Textur codiert.  
  
 Cubemaps  
 Cubemaps können unterschiedliche Arten von Daten enthalten – wie etwa Farben oder Normale – sind aber in Form von sechs Texturen auf den Flächen eines Würfels organisiert. Daher werden Cubemaps nicht durch die Angabe von Texturkoordinaten sondern durch Angabe eines Vektors dargestellt, dessen Ursprung das Zentrum des Würfels ist. Das Sample wird am Schnittpunkt des Vektors mit dem Würfel erfasst. Mithilfe von Cubemaps kann eine Näherung der Umgebung bereitgestellt werden, die zum Berechnen von Reflexionen dienen kann – das wird als *Environment Mapping*bezeichnet – oder um Texturen auf sphärischen Objekten mit geringerer Verzerrung zu darzustellen, als sie mit einfachen, zweidimensionalen Texturen erreicht werden kann.  
  
 Jede Textur kann auf verschiedene Weise codiert und komprimiert werden, die orthogonal zu der Art der in der Textur enthaltenen Daten oder ihrer Dimensionalität oder „Form“ ist. Allerdings ergeben verschiedene Codierungs- und Komprimierungsverfahren für verschiedene Arten von Daten unterschiedlich gute Ergebnisse.  
  
 Sie können die Bildbearbeitung verwenden, um Texturen und Bilder auf ähnliche Weise wie in anderen Bild-Editoren zu erstellen und zu bearbeiten. Die Bildbearbeitung bietet außerdem MipMaps und weitere Features für die Verwendung in der 3D-Grafik und unterstützt viele der stark komprimierten Texturformate mit Hardwarebeschleunigung, die von DirectX unterstützt werden.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Bildbearbeitung](../designers/image-editor.md)|Beschreibt die Verwendung der Bildbearbeitung für die Arbeit mit Texturen und Bildern.|  
|[Beispiele für die Bildbearbeitung](../designers/image-editor-examples.md)|Enthält Links zu Themen, in denen die Verwendung der Bildbearbeitung für das Ausführen häufiger Aufgaben der Bildverarbeitung veranschaulicht wird.|