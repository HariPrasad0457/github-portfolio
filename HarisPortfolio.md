import React, { useState, useEffect, useRef } from "react";

import { 

  Mail, 

  Phone, 

  MapPin,

  Github,

  Linkedin,

  Download,

  Code2,

  Database,

  Award,

  Briefcase,

  GraduationCap,

  ExternalLink,

  ChevronRight,

  Sparkles,

  Zap,

  Target,

  TrendingUp,

  Users,

  CheckCircle2,

  Star

} from "lucide-react";
import { Button } from "@/components/ui/button";

import { Badge } from "@/components/ui/badge";

import { Card, CardContent } from "@/components/ui/card";
import { motion, useScroll, useTransform, AnimatePresence } from "framer-motion";



export default function Home() {

  const [activeSection, setActiveSection] = useState("home");
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });

  const [isHovering, setIsHovering] = useState(false);
  const { scrollYProgress } = useScroll();

  const y = useTransform(scrollYProgress, [0, 1], ["0%", "100%"]);
  useEffect(() => {

    const handleMouseMove = (e) => {

      setMousePosition({ x: e.clientX, y: e.clientY });

    };

    window.addEventListener("mousemove", handleMouseMove);

    return () => window.removeEventListener("mousemove", handleMouseMove);

  }, []);
  const skills = [

    { name: "Python", level: 90, color: "from-yellow-400 to-yellow-600", icon: "🐍" },

    { name: "QGIS", level: 85, color: "from-green-400 to-green-600", icon: "🗺️" },

    { name: "Power BI", level: 80, color: "from-orange-400 to-orange-600", icon: "📊" },

    { name: "Java", level: 85, color: "from-red-400 to-red-600", icon: "☕" },

    { name: "Azure", level: 75, color: "from-blue-400 to-blue-600", icon: "☁️" },

    { name: "Data Analysis", level: 88, color: "from-purple-400 to-purple-600", icon: "📈" }

  ];
  const experiences = [

    {

      company: "Uber",

      role: "Operation Associate - SME & QC Reviewer",

      period: "Nov 2023 - Present",

      location: "Hyderabad, India",

      highlights: [

        "Led quality control initiatives for Uber's Living Maps team",

        "Mentored new associates and ensured high-accuracy GIS data",

        "Analyzed aerial/satellite imagery to update live maps",

   
        "Contributed to AI/ML data labeling and audits",

        "Generated model inputs for machine learning processes"

      ],

      color: "from-black to-gray-800"

    }

  ];
  const projects = [

    {

      title: "Restaurant Management System",

      description: "Command-line application for restaurant operations with order handling, billing, and menu management",

      tech: ["Core Java", "OOP", "File Handling"],

      icon: "🍽️",

      color: "from-orange-500 to-red-500"

    },

    {

      title: "Smart Footwear Energy Generator",

      description: "IoT solution with piezoelectric sensors generating electricity from walking motion",

      
      tech: ["IoT", "Sensor Data", "Data Analysis"],

      icon: "👟",

      color: "from-purple-500 to-pink-500"

    }

  ];
  const achievements = [

    { icon: <Award className="w-6 h-6" />, title: "Quality Excellence at Uber", desc: "Enhanced GIS data quality for millions of users" },

    { icon: <Target className="w-6 h-6" />, title: "SME Recognition", desc: "Subject Matter Expert for Living Maps team" },

    { icon: <Users className="w-6 h-6" />, title: "Team Leadership", desc: "Mentored and trained new associates" },

    { icon: <TrendingUp className="w-6 h-6" />, title: "Innovation", desc: "Contributed to AI/ML workflows" }

  ];
  return (

    <div className="min-h-screen bg-black text-white overflow-hidden relative">

      {/* Animated Background */}

      <div className="fixed inset-0 z-0">

        <div className="absolute inset-0 bg-gradient-to-br from-blue-900/20 via-purple-900/20 to-pink-900/20"></div>

        <div 

          className="absolute w-96 h-96 bg-blue-500/10 rounded-full blur-3xl"

          style={{

            left: `${mousePosition.x - 192}px`,

         
            top: `${mousePosition.y - 192}px`,

            transition: "all 0.3s ease-out"

          }}

        ></div>

        <div className="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAiIGhlaWdodD0iNjAiIHZpZXdCb3g9IjAgMCA2MCA2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48ZyBmaWxsPSJub25lIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiPjxwYXRoIGQ9Ik0zNiAxOGMzLjMxNCAwIDYgMi42ODYgNiA2cy0yLjY4NiA2LTYgNi02LTIuNjg2LTYtNiAyLjY4Ni02IDYtNnoiIHN0cm9rZT0iIzMzMyIgc3Ryb2tlLXdpZHRoPSIwLjUiLz48L2c+PC9zdmc+')] opacity-20"></div>

      </div>



      {/* Floating Navigation */}

      <motion.nav 

        initial={{ y: -100 }}

        animate={{ y: 0 }}

     
        className="fixed top-8 left-1/2 -translate-x-1/2 z-50 bg-white/5 backdrop-blur-xl border border-white/10 rounded-full px-8 py-4 shadow-2xl"

      >

        <div className="flex gap-8 items-center">

          <motion.div 

            whileHover={{ scale: 1.1, rotate: 360 }}

            transition={{ duration: 0.5 }}

            className="text-2xl font-bold bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent"

       
          >

            HPN

          </motion.div>

          {["Home", "About", "Skills", "Experience", "Projects", "Contact"].map((item) => (

            <motion.a

              key={item}

              href={`#${item.toLowerCase()}`}

              whileHover={{ scale: 1.1 }}

 
              className="text-sm font-medium text-white/70 hover:text-white transition-colors relative group"

            >

              {item}

              <motion.div 

                className="absolute -bottom-1 left-0 w-0 h-0.5 bg-gradient-to-r from-blue-400 to-purple-400 group-hover:w-full transition-all duration-300"

              
          ></motion.div>

            </motion.a>

          ))}

        </div>

      </motion.nav>



      {/* Hero Section */}

      <section id="home" className="min-h-screen flex items-center justify-center relative z-10 px-6">

        <div className="max-w-7xl w-full">

          <div className="grid lg:grid-cols-2 gap-16 items-center">

            {/* Left Content */}

  
            <motion.div

              initial={{ opacity: 0, x: -50 }}

              animate={{ opacity: 1, x: 0 }}

              transition={{ duration: 0.8 }}

            >

              <motion.div

         
                initial={{ opacity: 0, y: 20 }}

                animate={{ opacity: 1, y: 0 }}

                transition={{ delay: 0.2 }}

                className="mb-6"

              >

                <Badge className="mb-4 
                bg-gradient-to-r from-blue-500 to-purple-500 border-none text-white px-4 py-2">

                  <Sparkles className="w-4 h-4 mr-2" />

                  Available for Opportunities

                </Badge>

              </motion.div>



              <motion.div

        
                initial={{ opacity: 0, y: 20 }}

                animate={{ opacity: 1, y: 0 }}

                transition={{ delay: 0.3 }}

              >

                <h1 className="text-6xl lg:text-8xl font-bold mb-6">

             
                  <span className="block">Hari Prasad</span>

                  <span className="block bg-gradient-to-r from-blue-400 via-purple-400 to-pink-400 bg-clip-text text-transparent animate-gradient">

                    Nalajala

                  </span>

                </h1>

             
              </motion.div>



              <motion.div

                initial={{ opacity: 0, y: 20 }}

                animate={{ opacity: 1, y: 0 }}

                transition={{ delay: 0.4 }}

                className="space-y-4 mb-8"

       
              >

                <div className="flex items-center gap-3 text-xl">

                  <Zap className="w-6 h-6 text-yellow-400" />

                  <span className="text-gray-300">Technical Professional</span>

                </div>

               
                <div className="flex items-center gap-3 text-xl">

                  <Code2 className="w-6 h-6 text-blue-400" />

                  <span className="text-gray-300">GIS & Data Expert</span>

                </div>

                <div className="flex items-center gap-3 text-xl">

               
                  <Database className="w-6 h-6 text-purple-400" />

                  <span className="text-gray-300">Software Developer</span>

                </div>

              </motion.div>



              <motion.p

                initial={{ opacity: 0, y: 20 }}

        
                animate={{ opacity: 1, y: 0 }}

                transition={{ delay: 0.5 }}

                className="text-lg text-gray-400 mb-8 leading-relaxed max-w-xl"

              >

                Transforming data into insights and building innovative solutions.
                Specialized in GIS operations, quality control, and software development 

                with a passion for AI/ML applications.
              </motion.p>



              <motion.div

                initial={{ opacity: 0, y: 20 }}

                animate={{ opacity: 1, y: 0 }}

                transition={{ delay: 0.6 }}

                className="flex flex-wrap gap-4 mb-8"

      
              >

                <Button 

                  size="lg"

                  className="bg-gradient-to-r from-blue-500 to-purple-500 hover:from-blue-600 hover:to-purple-600 text-white border-none group"

                >

                
                  <a href="#contact" className="flex items-center gap-2">

                    Let's Connect

                    <ChevronRight className="w-5 h-5 group-hover:translate-x-1 transition-transform" />

                  </a>

                </Button>

              
                <Button 

                  size="lg"

                  variant="outline"

                  className="border-white/20 bg-white/5 hover:bg-white/10 text-white backdrop-blur-sm"

                >

                  <Download className="w-5 h-5 mr-2" />

 
                  Download Resume

                </Button>

              </motion.div>



              <motion.div

                initial={{ opacity: 0, y: 20 }}

                animate={{ 
                opacity: 1, y: 0 }}

                transition={{ delay: 0.7 }}

                className="flex gap-6"

              >

                <motion.div 

                  whileHover={{ scale: 1.1, y: -5 }}

      
                  className="flex items-center gap-2 text-gray-400"

                >

                  <MapPin className="w-5 h-5 text-blue-400" />

                  <span className="text-sm">Chirala, AP</span>

                </motion.div>

           
                <motion.div 

                  whileHover={{ scale: 1.1, y: -5 }}

                  className="flex items-center gap-2 text-gray-400"

                >

                  <Mail className="w-5 h-5 text-purple-400" />

            
                  <a href="mailto:harinalajala457@gmail.com" className="text-sm hover:text-white">

                    Email Me

                  </a>

                </motion.div>

                <motion.div 

                  whileHover={{ 
                  scale: 1.1, y: -5 }}

                  className="flex items-center gap-2 text-gray-400"

                >

                  <Phone className="w-5 h-5 text-pink-400" />

                  <a href="tel:+917330736775" className="text-sm hover:text-white">

                
                  Call Me

                  </a>

                </motion.div>

              </motion.div>

            </motion.div>



            {/* Right Content - Photo */}

            <motion.div

      
                initial={{ opacity: 0, scale: 0.8, rotateY: 90 }}

              animate={{ opacity: 1, scale: 1, rotateY: 0 }}

              transition={{ duration: 1, delay: 0.3 }}

              className="relative"

              onMouseEnter={() => setIsHovering(true)}

              onMouseLeave={() 
                () => setIsHovering(false)}

            >

              <div className="relative w-full max-w-lg mx-auto">

                {/* Animated Rings */}

                <motion.div

                  animate={{ rotate: 360 }}

             
                  transition={{ duration: 20, repeat: Infinity, ease: "linear" }}

                  className="absolute inset-0 rounded-full border-2 border-dashed border-blue-500/30"

                ></motion.div>

                <motion.div

                  animate={{ rotate: -360 }}

            
                  transition={{ duration: 25, repeat: Infinity, ease: "linear" }}

                  className="absolute inset-8 rounded-full border-2 border-dashed border-purple-500/30"

                ></motion.div>



                {/* Glowing Background */}

                <motion.div

             
                  animate={{ 

                    scale: isHovering ?
                    1.1 : 1,

                    rotate: isHovering ?
                    5 : 0

                  }}

                  className="absolute inset-0 bg-gradient-to-br from-blue-500 via-purple-500 to-pink-500 rounded-full blur-3xl opacity-40"

                ></motion.div>



                {/* Photo Container */}

                <motion.div

   
                animate={{ 

                    y: isHovering ?
                    -10 : 0,

                    scale: isHovering ?
                    1.05 : 1

                  }}

                  transition={{ duration: 0.3 }}

                  className="relative aspect-square rounded-full overflow-hidden border-4 border-white/10 shadow-2xl"

                >

                  <img 
 

                    src="https://qtrypzzcjebvfcihiynt.supabase.co/storage/v1/object/public/base44-prod/public/690de3a4dcb018692a160fdf/ef1d523d3_Screenshot2025-11-05205417.png" 

                    alt="Hari Prasad Nalajala"

                    className="w-full h-full object-cover"

                  />

                 
                  <div className="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent"></div>

                </motion.div>



                {/* Floating Stats */}

                <motion.div

                  initial={{ opacity: 0, x: -50 }}

                  animate={{ opacity: 
                  1, x: 0 }}

                  transition={{ delay: 1 }}

                  className="absolute -left-4 top-1/4 bg-white/10 backdrop-blur-xl border border-white/20 rounded-2xl p-4 shadow-xl"

                >

                  <div className="text-3xl font-bold bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">

        
                    90%

                  </div>

                  <div className="text-xs text-gray-400">Python Expert</div>

                </motion.div>



                <motion.div

                 
                  initial={{ opacity: 0, x: 50 }}

                  animate={{ opacity: 1, x: 0 }}

                  transition={{ delay: 1.2 }}

                  className="absolute -right-4 top-2/3 bg-white/10 backdrop-blur-xl border border-white/20 rounded-2xl p-4 shadow-xl"

                >

       
                  <div className="text-3xl font-bold bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">

                    Uber

                  </div>

                  <div className="text-xs text-gray-400">QC Expert</div>

                </motion.div>

       
              </div>

            </motion.div>

          </div>

        </div>

      </section>



      {/* Achievements Grid */}

      <section id="about" className="py-32 px-6 relative z-10">

        <div className="max-w-7xl mx-auto">

          <motion.div

            initial={{ opacity: 0, y: 30 
            }}

            whileInView={{ opacity: 1, y: 0 }}

            viewport={{ once: true }}

            className="text-center mb-16"

          >

            <h2 className="text-5xl lg:text-6xl font-bold mb-4">

              <span className="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">

          
                Key Achievements

              </span>

            </h2>

            <p className="text-gray-400 text-xl">Driving impact through innovation and excellence</p>

          </motion.div>



          <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-6">

            {achievements.map((achievement, index) => (

         
                <motion.div

                key={index}

                initial={{ opacity: 0, y: 30 }}

                whileInView={{ opacity: 1, y: 0 }}

                viewport={{ once: true }}

                transition={{ delay: 
                index * 0.1 }}

                whileHover={{ y: -10, scale: 1.05 }}

              >

                <Card className="bg-white/5 backdrop-blur-xl border-white/10 hover:border-white/20 transition-all h-full">

                  <CardContent className="p-6 text-center">

                    
                    <motion.div 

                      whileHover={{ rotate: 360, scale: 1.2 }}

                      transition={{ duration: 0.6 }}

                      className="w-16 h-16 bg-gradient-to-br from-blue-500 to-purple-500 rounded-2xl flex items-center justify-center mx-auto mb-4 text-white"

              
                      >

                      {achievement.icon}

                    </motion.div>

                    <h3 className="font-bold text-lg mb-2">{achievement.title}</h3>

                    <p className="text-gray-400 text-sm">{achievement.desc}</p>

       
                    </CardContent>

                </Card>

              </motion.div>

            ))}

          </div>

        </div>

      </section>



      {/* Skills Section */}

      <section id="skills" className="py-32 px-6 relative z-10">

   
        <div className="max-w-7xl mx-auto">

          <motion.div

            initial={{ opacity: 0, y: 30 }}

            whileInView={{ opacity: 1, y: 0 }}

            viewport={{ once: true }}

            className="text-center mb-16"

          >

           
            <h2 className="text-5xl lg:text-6xl font-bold mb-4">

              <span className="bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">

                Technical Arsenal

              </span>

            </h2>

            <p className="text-gray-400 text-xl">Mastering the tools that power innovation</p>

          </motion.div>



    
          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">

            {skills.map((skill, index) => (

              <motion.div

                key={skill.name}

                initial={{ opacity: 0, scale: 0.8 }}

                whileInView={{ opacity: 1, scale: 1 }}

   
                viewport={{ once: true }}

                transition={{ delay: index * 0.1 }}

                whileHover={{ scale: 1.05, y: -10 }}

              >

                <Card className="bg-white/5 backdrop-blur-xl border-white/10 hover:border-white/20 transition-all overflow-hidden group">

     
                  <CardContent className="p-6">

                    <div className="flex items-center justify-between mb-4">

                      <div className="flex items-center gap-3">

                        <motion.div 

            
                          whileHover={{ rotate: 360, scale: 1.3 }}

                          transition={{ duration: 0.5 }}

                          className="text-4xl"

                        >

  
                          {skill.icon}

                        </motion.div>

                        <span className="text-xl font-bold">{skill.name}</span>

                      </div>

    
                      <motion.span 

                        initial={{ scale: 0 }}

                        whileInView={{ scale: 1 }}

                        transition={{ delay: index 
                        * 0.1 + 0.3, type: "spring" }}

                        className="text-2xl font-bold bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent"

                      >

                        {skill.level}%

                  
                      </motion.span>

                    </div>

                    <div className="relative h-3 bg-white/10 rounded-full overflow-hidden">

                      <motion.div

                        initial={{ width: 0 }}

  
                        whileInView={{ width: `${skill.level}%` }}

                        viewport={{ once: true }}

                        transition={{ duration: 1.5, delay: index * 0.1, ease: "easeOut" }}

               
                        className={`h-full bg-gradient-to-r ${skill.color} relative`}

                      >

                        <motion.div

                          animate={{ x: ["-100%", "100%"] }}

            
                          transition={{ duration: 1.5, repeat: Infinity, ease: "linear" }}

                          className="absolute inset-0 bg-gradient-to-r from-transparent via-white/30 to-transparent"

                        ></motion.div>

                      </motion.div>

  
                      </div>

                  </CardContent>

                </Card>

              </motion.div>

            ))}

          </div>



          {/* Additional 
          Skills Tags */}

          <motion.div

            initial={{ opacity: 0, y: 30 }}

            whileInView={{ opacity: 1, y: 0 }}

            viewport={{ once: true }}

            className="mt-16 text-center"

          >

            <p className="text-gray-400 mb-6">Also proficient 
            in:</p>

            <div className="flex flex-wrap justify-center gap-3">

              {["Machine Learning", "GIS Analysis", "Data Visualization", "Quality Control", "Team Leadership", "Azure Cloud", "Core Java"].map((tag, index) => (

                <motion.div

                  key={tag}

                  initial={{ opacity: 
                  0, scale: 0 }}

                  whileInView={{ opacity: 1, scale: 1 }}

                  viewport={{ once: true }}

                  transition={{ delay: index * 0.05 }}

                  whileHover={{ scale: 1.1, y: -5 }}

       
                  >

                  <Badge className="px-4 py-2 bg-gradient-to-r from-blue-500/20 to-purple-500/20 border-white/20 text-white hover:from-blue-500/30 hover:to-purple-500/30">

                    {tag}

                  </Badge>

                </motion.div>

          
                ))}

            </div>

          </motion.div>

        </div>

      </section>



      {/* Experience Timeline */}

      <section id="experience" className="py-32 px-6 relative z-10">

        <div className="max-w-5xl mx-auto">

          <motion.div

            initial={{ opacity: 0, y: 30 }}

   
            whileInView={{ opacity: 1, y: 0 }}

            viewport={{ once: true }}

            className="text-center mb-16"

          >

            <h2 className="text-5xl lg:text-6xl font-bold mb-4">

              <span className="bg-gradient-to-r from-blue-400 via-purple-400 to-pink-400 bg-clip-text text-transparent">

            
                Professional Journey

              </span>

            </h2>

            <p className="text-gray-400 text-xl">Building the future, one innovation at a time</p>

          </motion.div>



          {experiences.map((exp, index) => (

            <motion.div

             
              key={index}

              initial={{ opacity: 0, x: -50 }}

              whileInView={{ opacity: 1, x: 0 }}

              viewport={{ once: true }}

              whileHover={{ scale: 1.02 }}

            >

              <Card 
              className="bg-gradient-to-br from-white/10 to-white/5 backdrop-blur-xl border-white/20 overflow-hidden mb-8">

                <div className={`h-2 bg-gradient-to-r ${exp.color}`}></div>

                <CardContent className="p-8">

                  <div className="flex flex-col lg:flex-row justify-between items-start lg:items-center mb-6">

                    <div>

             
                      <motion.h3 

                        whileHover={{ x: 10 }}

                        className="text-3xl font-bold mb-2"

                      >

               
                        {exp.role}

                      </motion.h3>

                      <p className="text-xl text-gray-300">{exp.company}</p>

                    </div>

                    <div className="text-right mt-4 lg:mt-0">

  
                      <p className="text-lg text-gray-400">{exp.period}</p>

                      <p className="text-sm text-gray-500 flex items-center gap-2 justify-end mt-1">

                        <MapPin className="w-4 h-4" />

                      
                        {exp.location}

                      </p>

                    </div>

                  </div>



                  <div className="space-y-3">

                   
                    {exp.highlights.map((highlight, idx) => (

                      <motion.div

                        key={idx}

                        initial={{ opacity: 0, x: -20 }}

                     
                        whileInView={{ opacity: 1, x: 0 }}

                        viewport={{ once: true }}

                        transition={{ delay: idx * 0.1 }}

                        whileHover={{ x: 10 }}

         
                        className="flex items-start gap-3 group"

                      >

                        <CheckCircle2 className="w-5 h-5 text-green-400 mt-1 flex-shrink-0 group-hover:scale-125 transition-transform" />

                        <p className="text-gray-300">{highlight}</p>

   
                      </motion.div>

                    ))}

                  </div>

                </CardContent>

              </Card>

            </motion.div>

 
            ))}



          {/* Education Card */}

          <motion.div

            initial={{ opacity: 0, y: 30 }}

            whileInView={{ opacity: 1, y: 0 }}

            viewport={{ once: true }}

            whileHover={{ scale: 1.02 }}

    
            >

            <Card className="bg-gradient-to-br from-purple-500/10 to-pink-500/10 backdrop-blur-xl border-purple-500/20">

              <CardContent className="p-8">

                <div className="flex items-start gap-6">

                  <motion.div

                    whileHover={{ rotate: 360, scale: 1.2 
                    }}

                    transition={{ duration: 0.6 }}

                    className="w-16 h-16 bg-gradient-to-br from-purple-500 to-pink-500 rounded-2xl flex items-center justify-center flex-shrink-0"

                  >

                    <GraduationCap className="w-8 h-8 text-white" />

      
                    </motion.div>

                  <div>

                    <h3 className="text-2xl font-bold mb-2">Bachelor's in Electronics and Communication Engineering</h3>

                    <p className="text-gray-300 mb-2">St.
                    Ann's College of Engineering and Technology</p>

                    <p className="text-gray-400">2019 - 2023 • Andhra Pradesh, India</p>

                  </div>

                </div>

              </CardContent>

            </Card>

        
          </motion.div>

        </div>

      </section>



      {/* Projects Showcase */}

      <section id="projects" className="py-32 px-6 relative z-10">

        <div className="max-w-7xl mx-auto">

          <motion.div

            initial={{ opacity: 0, y: 30 }}

            whileInView={{ opacity: 1, y: 0 }}

          
            viewport={{ once: true }}

            className="text-center mb-16"

          >

            <h2 className="text-5xl lg:text-6xl font-bold mb-4">

              <span className="bg-gradient-to-r from-orange-400 to-pink-400 bg-clip-text text-transparent">

                Featured Projects

              </span>

      
              </h2>

            <p className="text-gray-400 text-xl">Innovative solutions that make a difference</p>

          </motion.div>



          <div className="grid lg:grid-cols-2 gap-8">

            {projects.map((project, index) => (

              <motion.div

                key={index}

       
                initial={{ opacity: 0, y: 30 }}

                whileInView={{ opacity: 1, y: 0 }}

                viewport={{ once: true }}

                transition={{ delay: index * 0.2 }}

                whileHover={{ y: -15, scale: 1.02 }}

    
                >

                <Card className="bg-white/5 backdrop-blur-xl border-white/10 overflow-hidden h-full group">

                  <div className={`h-48 bg-gradient-to-br ${project.color} flex items-center justify-center relative overflow-hidden`}>

                    <motion.div

                      
                      animate={{ scale: [1, 1.2, 1] }}

                      transition={{ duration: 3, repeat: Infinity }}

                      className="text-8xl opacity-20"

                    >

                      {project.icon}

   
                      </motion.div>

                    <motion.div 

                      className="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent"

                      whileHover={{ opacity: 0 }}

           
                      ></motion.div>

                    <div className="absolute top-4 right-4">

                      <motion.div

                        whileHover={{ rotate: 45, scale: 1.2 }}

                 
                        className="w-10 h-10 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center"

                      >

                        <ExternalLink className="w-5 h-5" />

                      </motion.div>

               
                      </div>

                  </div>

                  <CardContent className="p-8">

                    <h3 className="text-2xl font-bold mb-4 group-hover:text-transparent group-hover:bg-clip-text group-hover:bg-gradient-to-r group-hover:from-blue-400 group-hover:to-purple-400 transition-all">

                      {project.title}

       
                      </h3>

                    <p className="text-gray-400 mb-6 leading-relaxed">

                      {project.description}

                    </p>

                    <div className="flex 
                    flex-wrap gap-2">

                      {project.tech.map((tech, idx) => (

                        <motion.div

                          key={tech}

                        
                          whileHover={{ scale: 1.1, y: -3 }}

                        >

                          <Badge className="bg-white/10 border-white/20 text-white hover:bg-white/20">

                            {tech}

           
                            </Badge>

                        </motion.div>

                      ))}

                    </div>

                  </CardContent>

 
                </Card>

              </motion.div>

            ))}

          </div>

        </div>

      </section>



      {/* Contact Section */}

      <section id="contact" className="py-32 px-6 relative z-10">

        <div className="max-w-4xl mx-auto text-center">

    
          <motion.div

            initial={{ opacity: 0, y: 30 }}

            whileInView={{ opacity: 1, y: 0 }}

            viewport={{ once: true }}

          >

            <h2 className="text-5xl lg:text-6xl font-bold mb-6">

              <span className="bg-gradient-to-r from-blue-400 via-purple-400 to-pink-400 
              bg-clip-text text-transparent">

                Let's Build Something Amazing

              </span>

            </h2>

            <p className="text-xl text-gray-400 mb-12">

              Ready to discuss your next project?
              I'm always open to new opportunities and
