# mon-site-ecommerce
from fpdf import FPDF

class PDF(FPDF):
    def header(self):
        self.set_font("Helvetica", "B", 14)
        self.cell(0, 10, "Comment gagner 100 EUR/mois à 16 ans (sans investir)", ln=True, align="C")
        self.ln(10)

    def chapter_title(self, title):
        self.set_font("Helvetica", "B", 12)
        self.set_text_color(0)
        self.cell(0, 10, title, ln=True)
        self.ln(4)

    def chapter_body(self, text):
        self.set_font("Helvetica", "", 11)
        self.multi_cell(0, 8, text)
        self.ln()

chapters = [
    ("Introduction", 
     "Tu veux gagner de l’argent mais tu n’as ni carte bancaire, ni capital, ni entreprise ? Bonne nouvelle : en 2025, tu peux commencer avec zéro euro. Cet ebook t’explique comment gagner tes premiers 100 EUR par mois sans rien investir, juste avec de la motivation et un smartphone."),
    
    ("1. Les règles avant de commencer",
     "- Tu ne deviens pas riche en 1 nuit, mais tu peux commencer petit\n"
     "- Sois sérieux : même sans argent, tu dois être régulier\n"
     "- Internet est ton terrain de jeu (TikTok, Insta, marketplaces...)\n"
     "- Ton objectif : utiliser ce que tu as déjà (temps, idées, téléphone)"),
    
    ("2. Revendre des objets autour de toi",
     "Regarde chez toi ou chez tes proches : livres, jeux, vêtements, accessoires. Prends-les en photo et mets-les en vente sur Leboncoin, Vinted, Facebook Marketplace. Tu peux facilement gagner 50 à 100 EUR par mois juste avec ça."),
    
    ("3. Affiliation + TikTok : 0 stock, 100% profit",
     "Tu n’as rien à vendre ? Utilise les produits des autres. Avec l'affiliation, tu reçois une commission à chaque vente. Crée un compte TikTok et fais des vidéos sur un produit (Amazon, Aliexpress, etc.). Mets ton lien affilié en bio. 1 vente = 2 à 10 EUR de commission."),
    
    ("4. Aider les autres avec tes compétences",
     "Tu es bon en rédaction, devoirs, graphisme ou réseaux ? Va sur 5euros.com ou Discord. Propose des petits services à 5-10 EUR. Exemple : corriger un devoir, créer une bio Insta, faire une miniature YouTube. Tu gagnes de l’argent en aidant."),
    
    ("5. Crée ton propre petit produit numérique",
     "Tu lis cet ebook ? Tu pourrais créer le tien. Choisis un sujet que tu maîtrises (skincare, sport, motivation, jeux...) et écris 3-4 pages. Transforme-le en PDF et vends-le sur Gumroad ou Ko-fi. C’est 100% gratuit, tu peux fixer ton prix (ex: 5 EUR)."),
    
    ("Conclusion : De 100 EUR à 500 EUR/mois",
     "Si tu appliques 2 ou 3 de ces méthodes sérieusement, tu peux dépasser les 100 EUR par mois. Ce n’est que le début. Une fois que tu as de l’expérience, tu peux faire évoluer tes idées : lancer un vrai site, une chaîne, ou automatiser ton business. Tu veux que je t’aide à passer au niveau supérieur ? Tu sais où me trouver.")
]

pdf = PDF()
pdf.set_auto_page_break(auto=True, margin=15)
pdf.add_page()

for title, body in chapters:
    pdf.chapter_title(title)
    pdf.chapter_body(body)

pdf_path = "/mnt/data/ebook_100euros_sans_investir.pdf"
pdf.output(pdf_path)

pdf_path
