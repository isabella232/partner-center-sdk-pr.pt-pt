---
title: Recursos de serviço geridos
description: Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos. Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ef644ac4d8ae9660cffc9558af33cc27832556c7
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768863"
---
# <a name="managed-service-resources"></a><span data-ttu-id="7422d-104">Recursos de serviço geridos</span><span class="sxs-lookup"><span data-stu-id="7422d-104">Managed service resources</span></span>

<span data-ttu-id="7422d-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="7422d-105">**Applies To**</span></span>

- <span data-ttu-id="7422d-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="7422d-106">Partner Center</span></span>
- <span data-ttu-id="7422d-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="7422d-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="7422d-108">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="7422d-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7422d-109">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7422d-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7422d-110">Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="7422d-110">Managed services are services to which a partner has delegated admin privileges.</span></span> <span data-ttu-id="7422d-111">Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.</span><span class="sxs-lookup"><span data-stu-id="7422d-111">Partners can provide support for and file service requests on the behalf of their managed services.</span></span>

## <a name="managedservice"></a><span data-ttu-id="7422d-112">Serviço Gerido</span><span class="sxs-lookup"><span data-stu-id="7422d-112">ManagedService</span></span>

<span data-ttu-id="7422d-113">Descreve um serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="7422d-113">Describes a managed service.</span></span>

| <span data-ttu-id="7422d-114">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7422d-114">Property</span></span>   | <span data-ttu-id="7422d-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="7422d-115">Type</span></span>                | <span data-ttu-id="7422d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7422d-116">Description</span></span>                                              |
|------------|---------------------|----------------------------------------------------------|
| <span data-ttu-id="7422d-117">Id</span><span class="sxs-lookup"><span data-stu-id="7422d-117">Id</span></span>         | <span data-ttu-id="7422d-118">string</span><span class="sxs-lookup"><span data-stu-id="7422d-118">string</span></span>              | <span data-ttu-id="7422d-119">O id de serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="7422d-119">The managed service id.</span></span>                                  |
| <span data-ttu-id="7422d-120">Nome</span><span class="sxs-lookup"><span data-stu-id="7422d-120">Name</span></span>       | <span data-ttu-id="7422d-121">string</span><span class="sxs-lookup"><span data-stu-id="7422d-121">string</span></span>              | <span data-ttu-id="7422d-122">O nome do serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="7422d-122">The name of the managed service.</span></span>                         |
| <span data-ttu-id="7422d-123">Nome do Grupo</span><span class="sxs-lookup"><span data-stu-id="7422d-123">GroupName</span></span>  | <span data-ttu-id="7422d-124">string</span><span class="sxs-lookup"><span data-stu-id="7422d-124">string</span></span>              | <span data-ttu-id="7422d-125">O nome do grupo a que pertence o serviço.</span><span class="sxs-lookup"><span data-stu-id="7422d-125">The name of the group to which the service belongs.</span></span>      |
| <span data-ttu-id="7422d-126">Ligações</span><span class="sxs-lookup"><span data-stu-id="7422d-126">Links</span></span>      | <span data-ttu-id="7422d-127">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="7422d-127">ManagedServiceLinks</span></span> | <span data-ttu-id="7422d-128">As ligações de recursos correspondentes ao serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="7422d-128">The resource links corresponding to the managed service.</span></span> |
| <span data-ttu-id="7422d-129">Atributos</span><span class="sxs-lookup"><span data-stu-id="7422d-129">Attributes</span></span> | <span data-ttu-id="7422d-130">RecursosTributos</span><span class="sxs-lookup"><span data-stu-id="7422d-130">ResourceAttributes</span></span>  | <span data-ttu-id="7422d-131">Os metadados atribuem correspondentes ao acordo.</span><span class="sxs-lookup"><span data-stu-id="7422d-131">The metadata attributes corresponding to the agreement.</span></span>  |

## <a name="managedservicelinks"></a><span data-ttu-id="7422d-132">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="7422d-132">ManagedServiceLinks</span></span>

<span data-ttu-id="7422d-133">Contém os links que permitem ao parceiro com permissões de administração delegadas fornecer suporte para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7422d-133">Contains the links that allow the partner with delegated admin permissions to provide support for the service.</span></span>

| <span data-ttu-id="7422d-134">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7422d-134">Property</span></span>      | <span data-ttu-id="7422d-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="7422d-135">Type</span></span> | <span data-ttu-id="7422d-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="7422d-136">Description</span></span>                 |
|---------------|------|-----------------------------|
| <span data-ttu-id="7422d-137">Serviço de Administração</span><span class="sxs-lookup"><span data-stu-id="7422d-137">AdminService</span></span>  | <span data-ttu-id="7422d-138">Ligação</span><span class="sxs-lookup"><span data-stu-id="7422d-138">Link</span></span> | <span data-ttu-id="7422d-139">O serviço de administração URI.</span><span class="sxs-lookup"><span data-stu-id="7422d-139">The admin service URI.</span></span>      |
| <span data-ttu-id="7422d-140">Saúde de Serviço</span><span class="sxs-lookup"><span data-stu-id="7422d-140">ServiceHealth</span></span> | <span data-ttu-id="7422d-141">Ligação</span><span class="sxs-lookup"><span data-stu-id="7422d-141">Link</span></span> | <span data-ttu-id="7422d-142">O serviço de saúde URI.</span><span class="sxs-lookup"><span data-stu-id="7422d-142">The service health URI.</span></span>     |
| <span data-ttu-id="7422d-143">ServiceTicket</span><span class="sxs-lookup"><span data-stu-id="7422d-143">ServiceTicket</span></span> | <span data-ttu-id="7422d-144">Ligação</span><span class="sxs-lookup"><span data-stu-id="7422d-144">Link</span></span> | <span data-ttu-id="7422d-145">O bilhete de serviço URI.</span><span class="sxs-lookup"><span data-stu-id="7422d-145">The service ticket URI.</span></span>     |
| <span data-ttu-id="7422d-146">Autónomo</span><span class="sxs-lookup"><span data-stu-id="7422d-146">Self</span></span>          | <span data-ttu-id="7422d-147">Ligação</span><span class="sxs-lookup"><span data-stu-id="7422d-147">Link</span></span> | <span data-ttu-id="7422d-148">O auto-URI.</span><span class="sxs-lookup"><span data-stu-id="7422d-148">The self URI.</span></span>               |
| <span data-ttu-id="7422d-149">Seguinte</span><span class="sxs-lookup"><span data-stu-id="7422d-149">Next</span></span>          | <span data-ttu-id="7422d-150">Ligação</span><span class="sxs-lookup"><span data-stu-id="7422d-150">Link</span></span> | <span data-ttu-id="7422d-151">A próxima página de artigos.</span><span class="sxs-lookup"><span data-stu-id="7422d-151">The next page of items.</span></span>     |
| <span data-ttu-id="7422d-152">Anterior</span><span class="sxs-lookup"><span data-stu-id="7422d-152">Previous</span></span>      | <span data-ttu-id="7422d-153">Ligação</span><span class="sxs-lookup"><span data-stu-id="7422d-153">Link</span></span> | <span data-ttu-id="7422d-154">A página anterior dos artigos.</span><span class="sxs-lookup"><span data-stu-id="7422d-154">The previous page of items.</span></span> |

