---
title: "Gewusst wie: Abrufen eines Diensts aus einem Hintergrundthread (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Multithreading, Dienste"
ms.assetid: 97a56709-66d4-431a-ae63-392ee5898511
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Gewusst wie: Abrufen eines Diensts aus einem Hintergrundthread (C++)
Dienste können nicht mithilfe `IServiceProvider.QueryService` von einem Hintergrundthread abgerufen werden.  Wenn Sie `QueryService` verwenden, um einen Dienst für den Hauptthread abzurufen und anschließend versuchen, den Dienst in einem Hintergrundthread zu verwenden, schlägt auch fehl.  
  
 Um einen Dienst von einem Hintergrundthread abzurufen, verwenden Sie `CoMarshalInterThreadInterfaceInStream` in der `IVsPackage.SetSite`\-Methode für den Dienstanbieter in einen Stream im Hauptthread zu marshallen.  Sie können den Dienstanbieter in einem Hintergrundthread dessen Marshalling rückgängig machen und verwenden anschließend den Dienst abzurufen.  Sie können nur einmal dessen Marshalling rückgängig machen, sodass die Schnittstelle zwischenspeichern, die Sie abrufen.  
  
> [!NOTE]
>  Verwalteter Code gemarshallt werden automatisch Schnittstellen zwischen Threads benötigt, damit das Abrufen eines Diensts von einem Hintergrundthread keine speziellen Code.  
  
## Beispiel  
 Der folgende Code marshallt einen Dienstanbieter im Hauptthread und bietet eine `QueryServiceFromBackgroundThread`\-Methode, um den Dienstanbieter dessen Marshalling rückgängig zu machen, um einen Dienst aus einem Hintergrundthread abzurufen.  
  
```  
class CMyPackage : public IVsPackage  
{  
private:  
    // Used to marshal IServiceProvider between threads  
    CComPtr< IStream > m_pSPStream;  
    // IServiceProvider proxy for the background thread  
    CComPtr< IServiceProvider > m_pBackgroundSP;  
  
public:  
    HRESULT SetSite( IServiceProvider* pSP )  
    {  
        // Marshal the service provider into a stream so that  
        // the background thread can retrieve it later  
        CoMarshalInterThreadInterfaceInStream(  
            IID_IServiceProvider, pSP, &m_pSPStream);  
  
        //... do the rest of your initialization  
    }  
  
    // Call this when your background thread needs to call QueryService  
    // The first time through, it unmarshals the interface stored   
    HRESULT QueryServiceFromBackgroundThread(  
        REFGUID rsid,        // [in] Service ID  
        REFIID riid,         // [in] Interface ID  
        // [out] Interface pointer of requested service (NULL on error)  
        void **ppvObj  
    {  
        if( !m_pBackgroundSP )  
        {  
            if( !m_pSPStream )  
            {  
                return E_UNEXPECTED;  
            }  
  
            HRESULT hr = CoGetInterfaceAndReleaseStream(   
                m_pSPStream, IID_IServiceProvider,   
                (void **)&m_pBackgroundSP );  
            if( FAILED(hr) )  
            {  
                return hr;  
            }  
  
            // The CoGetInterfaceAndReleaseStream has already   
            // destroyed the stream.  To avoid double-freeing,   
            // the smart wrapper needs to be detached.  
            m_pSPStream.Detach();  
        }  
  
        return m_pBackgroundSP->QueryService( rsid, riid, ppvObj );  
    }  
};  
```  
  
## Siehe auch  
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)