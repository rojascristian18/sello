# Módulo para Prestashop 1.6
Este módulo permite agregar una imagen a todos los productos que 
esten relacionados con la categoría registrada en el módulo.

Este módulo se muestra en el hook <b>displayProductListFunctionalButtons</b>.

# Configurar
Sí queremos que el sello se muestre en todas las páginas se debe modificar el 
archivo <b>product-list.tpl</b> de nuestro tema.

Buscar el bloque
```
  {if $page_name != 'index'}
    <div class="functional-buttons clearfix">
      {hook h='displayProductListFunctionalButtons' product=$product}
      {if isset($comparator_max_item) && $comparator_max_item}
        <div class="compare">
          <a class="add_to_compare" href="{$product.link|escape:'html':'UTF-8'}" data-id-product="{$product.id_product}">{l s='Add to Compare'}</a>
        </div>
      {/if}
    </div>
  {/if}
```
Luego reemplazar por
```
  {if $page_name != 'index'}
    <div class="functional-buttons clearfix">
      {hook h='displayProductListFunctionalButtons' product=$product}
      {if isset($comparator_max_item) && $comparator_max_item}
        <div class="compare">
          <a class="add_to_compare" href="{$product.link|escape:'html':'UTF-8'}" data-id-product="{$product.id_product}">{l s='Add to Compare'}</a>
        </div>
      {/if}
    </div>
  {else}
    {hook h='displayProductListFunctionalButtons' product=$product}
  {/if}
 ```
 
 Con estos cambios el sello se mostrará en el index tambien.
 
 <b>OJO, sí tienes algun otro módulo enlazado con el hook displayProductListFunctionalButtons, 
 tambien se mostrará en todos los productos y páginas.</b>
 
 Salud!