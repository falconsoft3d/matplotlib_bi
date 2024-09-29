# matplotlib_bi

# Line
```python
# Crear la figura y los ejes
fig, ax = plt.subplots()

# Definir los datos

sale_ids = self.env['sale.order'].search([])
sale_arrary_name = []
sale_arrary_amount_total = []
bar_labels = []
bar_colors = []

for sale in sale_ids:
    sale_arrary_name.append(sale.name)
    sale_arrary_amount_total.append(sale.amount_total)
    
    if sale.state == 'sale':
        bar_labels.append('Ordenes')
        bar_colors.append('tab:red')
    else:
        bar_labels.append('Presupuestos')
        bar_colors.append('tab:blue')
        

# Crear el gráfico de barras
ax.plot(sale_arrary_name, sale_arrary_amount_total)

# Agregar etiquetas y título
ax.set_ylabel('sale order')
ax.set_title('Ordenes de Ventas')
ax.legend(title='Ordenes de Venta')
ax.grid()


# Guardar la imagen en un buffer de memoria
buffer = BytesIO()
plt.savefig(buffer, format='png')  # Guardar la imagen en el buffer en formato PNG
plt.close(fig)
buffer.seek(0)  # Reiniciar el puntero del buffer
image_png = buffer.getvalue()
image_base64 = base64.b64encode(image_png).decode('utf-8')
buffer.close()
self.analysis_graph = image_base64
```
