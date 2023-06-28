# converts_csv_to_xml
# In this example, we use the csv module to read the CSV file and the xml.etree.ElementTree module to create and write the XML file.

import csv
import xml.etree.ElementTree as ET

def csv_to_xml(csv_file, xml_file):
    with open(csv_file, 'r') as file:
        csv_data = csv.reader(file)
        headers = next(csv_data)

        root = ET.Element('data')

        for row in csv_data:
            item = ET.SubElement(root, 'item')
            for idx, value in enumerate(row):
                ET.SubElement(item, headers[idx]).text = value

    tree = ET.ElementTree(root)
    tree.write(xml_file)

# Example usage
csv_to_xml('input.csv', 'output.xml')

