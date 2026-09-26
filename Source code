import React, { useState } from 'react';
import { 
  Home, 
  Briefcase, 
  User, 
  Image as ImageIcon, 
  Code2, 
  BookOpen, 
  Heart, 
  Gamepad2, 
  Pill, 
  ShoppingBag, 
  Plus, 
  Trash2, 
  X, 
  ExternalLink,
  Sparkles,
  Feather
} from 'lucide-react';

interface Project {
  id: string;
  title: string;
  category: string;
  description: string;
  tech: string[];
}

interface GalleryItem {
  id: string;
  title: string;
  url: string;
  caption: string;
}

export default function App() {
  // Page Navigation State
  const [activeTab, setActiveTab] = useState<string>('home');

  // Portfolio Data
  const codingLanguages = [
    { name: 'JavaScript', level: 'Novice', mastery: 45, icon: '⚡' },
    { name: 'Java', level: 'Novice', mastery: 40, icon: '☕' }
  ];

  const projects: Project[] = [
    {
      id: 'pharmacy',
      title: 'Pharmaceutical & Delivery Service Web App',
      category: 'Healthcare & Logistics',
      description: 'A full-stack web application for ordering prescriptions, managing inventory, and tracking door-to-door pharmaceutical delivery in real-time.',
      tech: ['JavaScript', 'HTML5', 'CSS3', 'REST API']
    },
    {
      id: 'medieval-shop',
      title: 'Medieval Marketplace & Guild Services',
      category: 'E-Commerce Website',
      description: 'An online shopping portal with a fantasy twist. Allows users to commission blacksmithing services, hire mercenary guards, and purchase potions and rare items.',
      tech: ['Java', 'SQL', 'UI Framework']
    },
    {
      id: 'multimode-boardgame',
      title: 'Multi-Mode Board Game Suite',
      category: 'Game Development',
      description: 'A unified digital tabletop engine featuring complete rule implementations and playable modes for Checkers, Chess, and Go with custom UI themes.',
      tech: ['JavaScript', 'HTML5 Canvas', 'Game Logic Engine']
    }
  ];

  // Gallery State (3 initial slots / interactive capability)
  const [galleryImages, setGalleryImages] = useState<GalleryItem[]>([
    {
      id: '1',
      title: 'World Map Sketch',
      url: 'https://images.unsplash.com/photo-1578632767115-351597cf2477?auto=format&fit=crop&w=800&q=80',
      caption: 'Initial mapping for my custom high-fantasy realm setting.'
    },
    {
      id: '2',
      title: 'Character Dossier',
      url: 'https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?auto=format&fit=crop&w=800&q=80',
      caption: 'Notes and character sheets from an ongoing tabletop campaign.'
    },
    {
      id: '3',
      title: 'Workspace & Code Setup',
      url: 'https://images.unsplash.com/photo-1555066931-4365d14bab8c?auto=format&fit=crop&w=800&q=80',
      caption: 'Late night coding sessions surrounded by story drafts and world-building outlines.'
    }
  ]);

  // Gallery Modal and Upload state
  const [selectedImage, setSelectedImage] = useState<GalleryItem | null>(null);
  const [newTitle, setNewTitle] = useState('');
  const [newUrl, setNewUrl] = useState('');
  const [newCaption, setNewCaption] = useState('');
  const [showAddModal, setShowAddModal] = useState(false);

  const handleAddImage = (e: React.FormEvent) => {
    e.preventDefault();
    if (!newTitle || !newUrl) return;
    
    const newEntry: GalleryItem = {
      id: Date.now().toString(),
      title: newTitle,
      url: newUrl,
      caption: newCaption || 'User added gallery photo'
    };

    setGalleryImages([...galleryImages, newEntry]);
    setNewTitle('');
    setNewUrl('');
    setNewCaption('');
    setShowAddModal(false);
  };

  const handleDeleteImage = (id: string, e: React.MouseEvent) => {
    e.stopPropagation();
    setGalleryImages(galleryImages.filter(img => img.id !== id));
    if (selectedImage?.id === id) {
      setSelectedImage(null);
    }
  };

  return (
    <div className="min-h-screen bg-[#0d021a] text-[#39ff14] font-sans selection:bg-[#ff6600] selection:text-black">
      {/* Dynamic CSS Styles for Custom Glows */}
      <style>{`
        .orange-glow {
          box-shadow: 0 0 15px rgba(255, 102, 0, 0.6), inset 0 0 10px rgba(255, 102, 0, 0.3);
        }
        .orange-glow-text {
          text-shadow: 0 0 8px rgba(255, 102, 0, 0.8), 0 0 20px rgba(255, 102, 0, 0.4);
        }
        .neon-green-glow {
          text-shadow: 0 0 10px rgba(57, 255, 20, 0.7);
        }
        .orange-border-glow {
          border-color: #ff6600;
          box-shadow: 0 0 12px #ff6600;
        }
      `}</style>

      {}
      <header className="sticky top-0 z-40 bg-[#140326]/90 backdrop-blur-md border-b-2 border-[#ff6600] shadow-[0_4px_20px_rgba(255,102,0,0.4)]">
        <div className="max-w-6xl mx-mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex items-center justify-between h-20">
            {/* Logo / Brand Name */}
            <div 
              onClick={() => setActiveTab('home')}
              className="flex items-center gap-3 cursor-pointer group"
            >
              <div className="p-2 bg-[#0d021a] rounded-lg border border-[#ff6600] group-hover:shadow-[0_0_15px_#ff6600] transition-all">
                <Sparkles className="w-6 h-6 text-[#ff6600] animate-pulse" />
              </div>
              <span className="text-xl sm:text-2xl font-black tracking-wider uppercase orange-glow-text text-[#39ff14]">
                NEON<span className="text-[#ff6600]">.DEV</span>
              </span>
            </div>

            {/* Navigation Tabs */}
            <nav className="flex space-x-1 sm:space-x-3">
              {[
                { id: 'home', label: 'Index', route: '/', icon: Home },
                { id: 'portfolio', label: 'Portfolio', route: '/portfolio', icon: Briefcase },
                { id: 'about', label: 'About', route: '/about', icon: User },
                { id: 'gallery', label: 'Gallery', route: '/gallery', icon: ImageIcon }
              ].map((tab) => {
                const Icon = tab.icon;
                const isActive = activeTab === tab.id;
                return (
                  <button
                    key={tab.id}
                    onClick={() => setActiveTab(tab.id)}
                    className={`flex items-center gap-2 px-3 py-2 sm:px-4 sm:py-2.5 rounded-lg font-bold text-xs sm:text-sm tracking-wide transition-all duration-300 border ${
                      isActive
                        ? 'bg-[#ff6600] text-black border-[#ff6600] shadow-[0_0_20px_#ff6600]'
                        : 'bg-[#1a0533] text-[#39ff14] border-[#39ff14]/30 hover:border-[#ff6600] hover:text-[#ff6600] hover:shadow-[0_0_10px_#ff6600]'
                    }`}
                  >
                    <Icon className={`w-4 h-4 ${isActive ? 'text-black' : 'text-[#39ff14]'}`} />
                    <span className="hidden md:inline">{tab.label}</span>
                    <span className="text-[10px] opacity-60 hidden lg:inline">({tab.route})</span>
                  </button>
                );
              })}
            </nav>
          </div>
        </div>
      </header>

      {/* Main Content Container */}
      <main className="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-10">

        {}
        {activeTab === 'home' && (
          <div className="space-y-12">
            {/* Hero Banner */}
            <section className="relative overflow-hidden rounded-2xl bg-[#140326] border-2 border-[#ff6600] p-8 sm:p-12 orange-glow">
              <div className="relative z-10 space-y-6 max-w-3xl">
                <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-[#0d021a] border border-[#39ff14] text-xs font-mono">
                  <span className="w-2 h-2 rounded-full bg-[#39ff14] animate-ping" />
                  Route: / (Index)
                </div>
                <h1 className="text-4xl sm:text-6xl font-black tracking-tight leading-tight orange-glow-text text-[#39ff14]">
                  WELCOME TO THE <br />
                  <span className="text-[#ff6600]">NEON REALM</span>
                </h1>
                <p className="text-lg text-[#39ff14]/90 font-mono leading-relaxed">
                  Interactive digital portal built with Next.js architecture. Explore my school programming projects, high-fantasy narrative worldbuilding, personal bio, and visual gallery.
                </p>
                <div className="flex flex-wrap gap-4 pt-4">
                  <button
                    onClick={() => setActiveTab('portfolio')}
                    className="flex items-center gap-2 px-6 py-3 rounded-xl font-bold bg-[#ff6600] text-black shadow-[0_0_15px_#ff6600] hover:bg-[#ff8533] transition-all"
                  >
                    <Briefcase className="w-5 h-5" /> View Portfolio
                  </button>
                  <button
                    onClick={() => setActiveTab('about')}
                    className="flex items-center gap-2 px-6 py-3 rounded-xl font-bold bg-[#0d021a] text-[#39ff14] border border-[#39ff14] hover:border-[#ff6600] hover:text-[#ff6600] hover:shadow-[0_0_15px_#ff6600] transition-all"
                  >
                    <User className="w-5 h-5" /> About Me
                  </button>
                </div>
              </div>
            </section>

            {/* Quick Access Cards */}
            <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div 
                onClick={() => setActiveTab('portfolio')}
                className="cursor-pointer group p-6 rounded-xl bg-[#140326] border border-[#39ff14]/30 hover:border-[#ff6600] transition-all hover:-translate-y-1 hover:shadow-[0_0_20px_rgba(255,102,0,0.5)]"
              >
                <Code2 className="w-10 h-10 text-[#ff6600] mb-4 group-hover:scale-110 transition-transform" />
                <h3 className="text-xl font-bold mb-2 text-[#39ff14]">School Projects</h3>
                <p className="text-sm font-mono text-[#39ff14]/80">
                  Java & JavaScript web apps, online shopping, delivery services & board games.
                </p>
              </div>

              <div 
                onClick={() => setActiveTab('about')}
                className="cursor-pointer group p-6 rounded-xl bg-[#140326] border border-[#39ff14]/30 hover:border-[#ff6600] transition-all hover:-translate-y-1 hover:shadow-[0_0_20px_rgba(255,102,0,0.5)]"
              >
                <BookOpen className="w-10 h-10 text-[#ff6600] mb-4 group-hover:scale-110 transition-transform" />
                <h3 className="text-xl font-bold mb-2 text-[#39ff14]">Worldbuilding & Bio</h3>
                <p className="text-sm font-mono text-[#39ff14]/80">
                  Over 3 million words written across lore documents, D&D campaigns & stories.
                </p>
              </div>

              <div 
                onClick={() => setActiveTab('gallery')}
                className="cursor-pointer group p-6 rounded-xl bg-[#140326] border border-[#39ff14]/30 hover:border-[#ff6600] transition-all hover:-translate-y-1 hover:shadow-[0_0_20px_rgba(255,102,0,0.5)]"
              >
                <ImageIcon className="w-10 h-10 text-[#ff6600] mb-4 group-hover:scale-110 transition-transform" />
                <h3 className="text-xl font-bold mb-2 text-[#39ff14]">Interactive Gallery</h3>
                <p className="text-sm font-mono text-[#39ff14]/80">
                  3 image capacity layout with dynamic image additions, deletions, and preview modals.
                </p>
              </div>
            </div>
          </div>
        )}

        {}
        {activeTab === 'portfolio' && (
          <div className="space-y-10">
            {/* Header */}
            <div className="border-b border-[#ff6600] pb-4 flex flex-col sm:flex-row justify-between items-start sm:items-end gap-2">
              <div>
                <h2 className="text-3xl font-black orange-glow-text text-[#39ff14]">PORTFOLIO</h2>
                <p className="text-sm font-mono text-[#39ff14]/80">Route: /portfolio</p>
              </div>
              <span className="text-xs bg-[#ff6600] text-black px-3 py-1 font-bold rounded-full">Academic Projects</span>
            </div>

            {/* Language Skills Section */}
            <div className="p-6 rounded-xl bg-[#140326] border border-[#ff6600] orange-glow space-y-4">
              <h3 className="text-xl font-bold text-[#ff6600] flex items-center gap-2">
                <Code2 className="w-5 h-5" /> Programming Languages
              </h3>
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                {codingLanguages.map((lang) => (
                  <div key={lang.name} className="p-4 rounded-lg bg-[#0d021a] border border-[#39ff14]/30 space-y-2">
                    <div className="flex justify-between items-center">
                      <span className="font-bold text-lg flex items-center gap-2">
                        <span>{lang.icon}</span> {lang.name}
                      </span>
                      <span className="text-xs font-mono text-[#ff6600] border border-[#ff6600] px-2 py-0.5 rounded">
                        {lang.level}
                      </span>
                    </div>
                    <div className="w-full bg-[#1a0533] h-3 rounded-full overflow-hidden border border-[#39ff14]/20">
                      <div 
                        className="bg-gradient-to-r from-[#39ff14] to-[#ff6600] h-full transition-all duration-500"
                        style={{ width: `${lang.mastery}%` }}
                      />
                    </div>
                  </div>
                ))}
              </div>
            </div>

            {/* Projects List */}
            <div className="space-y-6">
              <h3 className="text-2xl font-bold text-[#39ff14]">Featured School Projects</h3>
              <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
                {projects.map((project) => (
                  <div 
                    key={project.id} 
                    className="flex flex-col justify-between p-6 rounded-xl bg-[#140326] border border-[#39ff14]/30 hover:border-[#ff6600] transition-all hover:shadow-[0_0_20px_rgba(255,102,0,0.4)]"
                  >
                    <div className="space-y-4">
                      <div className="w-12 h-12 rounded-lg bg-[#0d021a] border border-[#ff6600] flex items-center justify-center text-[#ff6600]">
                        {project.id === 'pharmacy' && <Pill className="w-6 h-6" />}
                        {project.id === 'medieval-shop' && <ShoppingBag className="w-6 h-6" />}
                        {project.id === 'multimode-boardgame' && <Gamepad2 className="w-6 h-6" />}
                      </div>
                      <span className="text-xs font-mono text-[#ff6600] uppercase tracking-wider">{project.category}</span>
                      <h4 className="text-xl font-bold text-[#39ff14] leading-snug">{project.title}</h4>
                      <p className="text-sm font-mono text-[#39ff14]/80 leading-relaxed">{project.description}</p>
                    </div>

                    <div className="pt-6 mt-6 border-t border-[#39ff14]/20 flex flex-wrap gap-2">
                      {project.tech.map((t) => (
                        <span key={t} className="text-[11px] font-mono px-2 py-1 rounded bg-[#0d021a] text-[#39ff14] border border-[#39ff14]/40">
                          {t}
                        </span>
                      ))}
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {}
        {activeTab === 'about' && (
          <div className="space-y-8">
            {/* Header */}
            <div className="border-b border-[#ff6600] pb-4 flex flex-col sm:flex-row justify-between items-start sm:items-end gap-2">
              <div>
                <h2 className="text-3xl font-black orange-glow-text text-[#39ff14]">ABOUT ME</h2>
                <p className="text-sm font-mono text-[#39ff14]/80">Route: /about (Informal Bio)</p>
              </div>
              <span className="text-xs bg-[#ff6600] text-black px-3 py-1 font-bold rounded-full">Personal Profile</span>
            </div>

            {/* Informal Bio Card */}
            <div className="p-6 sm:p-8 rounded-2xl bg-[#140326] border-2 border-[#ff6600] orange-glow space-y-6">
              <div className="flex items-center gap-4">
                <div className="w-16 h-16 rounded-full bg-[#ff6600] text-black font-black text-2xl flex items-center justify-center border-2 border-[#39ff14]">
                  ME
                </div>
                <div>
                  <h3 className="text-2xl font-bold text-[#39ff14]">Hello there! 👋</h3>
                  <p className="text-sm font-mono text-[#ff6600]">Writer • Worldbuilder • Novice Programmer</p>
                </div>
              </div>

              <div className="p-4 rounded-xl bg-[#0d021a] border border-[#39ff14]/30 space-y-3 font-mono text-sm leading-relaxed text-[#39ff14]">
                <p>
                  Hey, welcome to my informal corner of the site! To keep it completely real with you: 
                  I am diagnosed <span className="text-[#ff6600] font-bold">Autistic</span>, <span className="text-[#ff6600] font-bold">Depressed</span>, and <span className="text-[#ff6600] font-bold">Bipolar</span>. 
                  Navigating the world through this lens gives me a unique perspective, standard hyperfocus tendencies, and an absolute passion for my creative hobbies.
                </p>
              </div>

              {/* Hobbies & Highlights Grid */}
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6 pt-2">
                {/* Writing Achievement */}
                <div className="p-5 rounded-xl bg-[#0d021a] border border-[#ff6600] space-y-3">
                  <div className="flex items-center gap-2 text-[#ff6600]">
                    <Feather className="w-6 h-6" />
                    <h4 className="font-bold text-lg text-[#39ff14]">3+ Million Word Archive</h4>
                  </div>
                  <p className="text-xs font-mono text-[#39ff14]/80 leading-relaxed">
                    I have written over 3,000,000 words inside Microsoft Word documents dedicated entirely to original fantasy lore, extensive worldbuilding, character arcs, and narrative story manuscripts.
                  </p>
                </div>

                {/* Tabletop & Reading */}
                <div className="p-5 rounded-xl bg-[#0d021a] border border-[#39ff14]/40 space-y-3">
                  <div className="flex items-center gap-2 text-[#39ff14]">
                    <Gamepad2 className="w-6 h-6 text-[#ff6600]" />
                    <h4 className="font-bold text-lg text-[#39ff14]">D&D & Reading</h4>
                  </div>
                  <p className="text-xs font-mono text-[#39ff14]/80 leading-relaxed">
                    Huge fan of Dungeons & Dragons (both DMing and playing), immersing myself in fantasy literature, listening to eclectic music tracks, and constantly expanding my universe concepts.
                  </p>
                </div>
              </div>
            </div>
          </div>
        )}

        {}
        {activeTab === 'gallery' && (
          <div className="space-y-8">
            {/* Header */}
            <div className="border-b border-[#ff6600] pb-4 flex flex-col sm:flex-row justify-between items-start sm:items-end gap-4">
              <div>
                <h2 className="text-3xl font-black orange-glow-text text-[#39ff14]">GALLERY</h2>
                <p className="text-sm font-mono text-[#39ff14]/80">Route: /gallery (Interactive Showcase)</p>
              </div>
              <button
                onClick={() => setShowAddModal(true)}
                className="flex items-center gap-2 px-4 py-2 rounded-lg bg-[#ff6600] text-black font-bold hover:bg-[#ff8533] shadow-[0_0_15px_#ff6600] transition-all text-sm"
              >
                <Plus className="w-4 h-4" /> Add New Picture
              </button>
            </div>

            {/* Gallery Image Grid */}
            <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
              {galleryImages.map((img) => (
                <div
                  key={img.id}
                  onClick={() => setSelectedImage(img)}
                  className="group relative rounded-xl bg-[#140326] border border-[#39ff14]/40 overflow-hidden cursor-pointer hover:border-[#ff6600] hover:shadow-[0_0_20px_#ff6600] transition-all flex flex-col"
                >
                  <div className="relative aspect-video overflow-hidden bg-[#0d021a]">
                    <img 
                      src={img.url} 
                      alt={img.title} 
                      className="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
                    />
                    <button
                      onClick={(e) => handleDeleteImage(img.id, e)}
                      className="absolute top-2 right-2 p-1.5 rounded-md bg-black/80 text-red-400 hover:text-red-200 border border-red-500/50 hover:border-red-500 transition-all opacity-0 group-hover:opacity-100"
                      title="Remove picture"
                    >
                      <Trash2 className="w-4 h-4" />
                    </button>
                  </div>
                  <div className="p-4 flex-1 flex flex-col justify-between space-y-2">
                    <div>
                      <h4 className="font-bold text-lg text-[#39ff14] group-hover:text-[#ff6600] transition-colors">{img.title}</h4>
                      <p className="text-xs font-mono text-[#39ff14]/70 line-clamp-2 mt-1">{img.caption}</p>
                    </div>
                    <span className="text-[10px] font-mono text-[#ff6600] flex items-center gap-1 pt-2">
                      Click to expand <ExternalLink className="w-3 h-3" />
                    </span>
                  </div>
                </div>
              ))}
            </div>

            {galleryImages.length === 0 && (
              <div className="text-center py-16 p-8 rounded-xl bg-[#140326] border border-dashed border-[#ff6600] space-y-4">
                <ImageIcon className="w-12 h-12 text-[#ff6600] mx-auto opacity-50" />
                <p className="font-mono text-[#39ff14]">No images in gallery. Click "Add New Picture" above to upload or embed standard links.</p>
              </div>
            )}
          </div>
        )}

      </main>

      {}
      {selectedImage && (
        <div className="fixed inset-0 z-50 bg-black/90 backdrop-blur-md flex items-center justify-center p-4">
          <div className="relative max-w-3xl w-full bg-[#140326] border-2 border-[#ff6600] rounded-2xl overflow-hidden orange-glow">
            <button
              onClick={() => setSelectedImage(null)}
              className="absolute top-4 right-4 z-10 p-2 rounded-full bg-black/80 text-[#39ff14] border border-[#39ff14] hover:border-[#ff6600] hover:text-[#ff6600]"
            >
              <X className="w-6 h-6" />
            </button>
            <div className="max-h-[60vh] overflow-hidden bg-black flex items-center justify-center">
              <img src={selectedImage.url} alt={selectedImage.title} className="max-h-[60vh] w-auto object-contain" />
            </div>
            <div className="p-6 space-y-2">
              <h3 className="text-2xl font-bold text-[#ff6600]">{selectedImage.title}</h3>
              <p className="text-sm font-mono text-[#39ff14]">{selectedImage.caption}</p>
            </div>
          </div>
        </div>
      )}

      {}
      {showAddModal && (
        <div className="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm flex items-center justify-center p-4">
          <div className="relative max-w-md w-full bg-[#140326] border-2 border-[#39ff14] rounded-xl p-6 space-y-4 shadow-[0_0_25px_#39ff14]">
            <div className="flex justify-between items-center border-b border-[#39ff14]/30 pb-3">
              <h3 className="text-xl font-bold text-[#39ff14] flex items-center gap-2">
                <Plus className="w-5 h-5 text-[#ff6600]" /> Add Picture to Gallery
              </h3>
              <button onClick={() => setShowAddModal(false)} className="text-[#39ff14] hover:text-[#ff6600]">
                <X className="w-5 h-5" />
              </button>
            </div>

            <form onSubmit={handleAddImage} className="space-y-4">
              <div>
                <label className="block text-xs font-mono text-[#ff6600] mb-1">Image Title</label>
                <input
                  type="text"
                  required
                  value={newTitle}
                  onChange={(e) => setNewTitle(e.target.value)}
                  placeholder="e.g. Map Design #2"
                  className="w-full bg-[#0d021a] border border-[#39ff14]/50 rounded p-2 text-sm text-[#39ff14] focus:border-[#ff6600] focus:outline-none"
                />
              </div>

              <div>
                <label className="block text-xs font-mono text-[#ff6600] mb-1">Image URL</label>
                <input
                  type="url"
                  required
                  value={newUrl}
                  onChange={(e) => setNewUrl(e.target.value)}
                  placeholder="https://images.unsplash.com/..."
                  className="w-full bg-[#0d021a] border border-[#39ff14]/50 rounded p-2 text-sm text-[#39ff14] focus:border-[#ff6600] focus:outline-none"
                />
              </div>

              <div>
                <label className="block text-xs font-mono text-[#ff6600] mb-1">Caption / Description</label>
                <textarea
                  rows={3}
                  value={newCaption}
                  onChange={(e) => setNewCaption(e.target.value)}
                  placeholder="Brief story or lore snippet about this image..."
                  className="w-full bg-[#0d021a] border border-[#39ff14]/50 rounded p-2 text-sm text-[#39ff14] focus:border-[#ff6600] focus:outline-none"
                />
              </div>

              <div className="flex justify-end gap-3 pt-2">
                <button
                  type="button"
                  onClick={() => setShowAddModal(false)}
                  className="px-4 py-2 rounded bg-[#0d021a] text-[#39ff14] border border-[#39ff14]/40 text-xs font-mono"
                >
                  Cancel
                </button>
                <button
                  type="submit"
                  className="px-4 py-2 rounded bg-[#ff6600] text-black font-bold text-xs hover:bg-[#ff8533] shadow-[0_0_10px_#ff6600]"
                >
                  Add Picture
                </button>
              </div>
            </form>
          </div>
        </div>
      )}

      {/* Footer */}
      <footer className="mt-20 border-t border-[#39ff14]/20 bg-[#140326] py-6 text-center text-xs font-mono text-[#39ff14]/60">
        <p>NextJS Neon Application • Custom Styling with Deep Purple Background & Orange Glow</p>
      </footer>
    </div>
  );
}
