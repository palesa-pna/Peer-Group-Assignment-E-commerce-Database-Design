1️⃣ ERD (Entity Relationship Diagram) Specification
Entities & Attributes (Expanded from Schema)
🏷️ Brand

id (PK)

name

description

logo_url

website_url

created_at

updated_at

🗂️ Product Category (self-referencing hierarchy)

id (PK)

name

description

parent_category_id (FK to self)

created_at

updated_at

📦 Product

id (PK)

name

description

brand_id (FK to Brand)

category_id (FK to Product Category)

base_price

is_active

created_at

updated_at

🖼️ Product Image

id (PK)

product_id (FK to Product)

image_url

alt_text

is_primary

display_order

created_at

🎨 Color

id (PK)

name

hex_code

created_at

📏 Size Category

id (PK)

name

description

created_at

📐 Size Option

id (PK)

size_category_id (FK to Size Category)

value

description

created_at

📚 Attribute Category

id (PK)

name

description

created_at

🧪 Attribute Type

id (PK)

name

description

created_at

🧵 Product Attribute

id (PK)

product_id (FK to Product)

attribute_category_id (FK to Attribute Category)

attribute_type_id (FK to Attribute Type)

name

value

created_at

🔄 Product Variation

id (PK)

product_id (FK to Product)

name

created_at

🧾 Product Item (SKU)

id (PK)

product_id (FK to Product)

sku (unique)

price

quantity_in_stock

color_id (FK to Color)

size_option_id (FK to Size Option)

is_active

created_at

updated_at

Product Item Variation (Junction)

product_item_id (FK to Product Item)

variation_id (FK to Product Variation)

variation_value

(Composite PK: product_item_id + variation_id)

Relationships
Brand → Product: One-to-Many (One brand has many products)

Product Category → Product: One-to-Many (One category has many products)

Product Category → Product Category: Self-referential (Parent-child hierarchy)

Product → Product Image: One-to-Many (One product has many images)

Product → Product Item: One-to-Many (One product has many SKUs)

Product → Product Attribute: One-to-Many (One product has many attributes)

Product → Product Variation: One-to-Many (One product has many variation types)

Size Category → Size Option: One-to-Many (One size category has many size options)

Product Item → Color: Many-to-One (Many SKUs can share one color)

Product Item → Size Option: Many-to-One (Many SKUs can share one size)

Product Item ↔ Product Variation: Many-to-Many via junction table (SKUs can have multiple variations)# Peer-Group-Assignment-E-commerce-Database-Design
