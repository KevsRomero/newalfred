#!/bin/bash

instances=(
    '{"name": "Matera CSS Homologacion", "ip": "10.63.75.144"}',
    '{"name": "Matera CSS Produccion", "ip": "10.63.75.164"}',
    '{"name": "Mulesoft Dev", "ip": "10.64.115.12"}',
    '{"name": "Mulesoft Prd", "ip": "10.64.113.16"}',
    '{"name": "IBM - DC Control", "ip": "10.64.115.36"}',
    '{"name": "SIGIR Neosoft Desarrollo", "ip": "10.64.115.60"}',
    '{"name": "SIGIR Neosoft Produccion", "ip": "10.64.113.85"}',
    '{"name": "Trade And Track Desarollo", "ip": "10.64.115.55"}',
    '{"name": "Trade And Track Produccion", "ip": "10.64.113.12"}',
    '{"name": "Matera DB PRD", "ip": "10.63.75.190"}',
    '{"name": "Celonis", "ip": "10.64.113.108"}'
)

eval $(ssh-agent)
ssh-add -D

echo "==============================================================="
echo "| Ingrese el numero de la Instancia a la que desea conectar:   |"
echo "==============================================================="
for i in "${!instances[@]}"; do
    name=$(echo "${instances[$i]}" | awk -F'"' '{print $4}')
    printf "%2d - %s\n" "$((i + 1))" "$name"
done
echo "==============================================================="

read -r selection
selected_instance=${instances[$((selection - 1))]}

ip=$(echo "$selected_instance" | awk -F'"' '{print $8}')
name=$(echo "$selected_instance" | awk -F'"' '{print $4}')

echo "Conectando a $name ($ip)"
ssh -tt -A batman.adminml.com fpstech@"$ip"
