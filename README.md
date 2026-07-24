import React from 'react';
import { Link } from 'react-router-dom';
import { MapPin, Phone, Mail, Heart, Users } from 'lucide-react';
import Hero from '../components/Hero';
import ServiceCard from '../components/ServiceCard';
import MinistryCard from '../components/MinistryCard';
import SermonCard from '../components/SermonCard';
import EventCard from '../components/EventCard';
import { churchInfo } from '../config/churchConfig';
import { services } from '../data/services';
import { ministries } from '../data/ministries';
import { sermons } from '../data/sermons';
import { events } from '../data/events';
import '../styles/Pages.css';

/**
 * HOME PAGE
 * Displays hero, upcoming events, ministries, sermons, testimonials, etc.
 */

export default function Home() {
  // Get featured/latest content
  const upcomingEvents = events.slice(0, 3);
  const latestSermons = sermons.slice(0, 3);
  const featuredMinistries = ministries.slice(0, 4);
  const mainServices = services.slice(0, 3);

  return (
    <main>
      {/* Hero Section */}
      <Hero />

      {/* Quick Actions */}
      <section className="quick-actions">
        <div className="container">
          <div className="actions-grid">
            <div className="action-card">
              <Phone className="action-icon" />
              <h3>Call Us</h3>
              <p>{churchInfo.phone}</p>
            </div>
            <div className="action-card">
              <Mail className="action-icon" />
              <h3>Email Us</h3>
              <p>{churchInfo.email}</p>
            </div>
            <div className="action-card">
              <MapPin className="action-icon" />
              <h3>Visit Us</h3>
              <p>{churchInfo.address}</p>
            </div>
          </div>
        </div>
      </section>

      {/* About Section */}
      <section className="about-preview section-light">
        <div className="container">
          <div className="section-title">
            <h2>Who We Are</h2>
            <p>Discover our mission and vision</p>
          </div>
          <div className="about-content">
            <div className="about-text">
              <h3>Living Faith Community Church Kenya</h3>
              <p>
                We are a Christ-centered community dedicated to spreading the Gospel, building strong families, 
                and transforming lives through the Word of God. Our vision is to impact our city and nation with 
                the love and grace of Jesus Christ.
              </p>
              <p>
                Whether you're new to faith or a lifelong believer, we welcome you to join our vibrant community. 
                We believe in authentic worship, biblical teaching, and practical faith that changes lives.
              </p>
              <Link to="/about" className="btn btn-primary">
                Learn More About Us
              </Link>
            </div>
            <div className="about-stats">
              <div className="stat">
                <div className="stat-number">15+</div>
                <div className="stat-label">Years of Ministry</div>
              </div>
              <div className="stat">
                <div className="stat-number">8</div>
                <div className="stat-label">Active Ministries</div>
              </div>
              <div className="stat">
                <div className="stat-number">1000+</div>
                <div className="stat-label">Church Members</div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Services Section */}
      <section className="services-section">
        <div className="container">
          <div className="section-title">
            <h2>Our Service Times</h2>
            <p>Join us for worship and fellowship</p>
          </div>
          <div className="grid grid-3">
            {mainServices.map((service) => (
              <ServiceCard key={service.id} service={service} />
            ))}
          </div>
          <div className="text-center mt-4">
            <Link to="/services" className="btn btn-primary">
              View All Services
            </Link>
          </div>
        </div>
      </section>

      {/* Pastor Section */}
      <section className="pastor-section section-light">
        <div className="container">
          <div className="pastor-content">
            <div className="pastor-image">
              <img 
                src={churchInfo.pastor.photo}
                alt={churchInfo.pastor.name}
                className="pastor-photo"
                onError={(e) => e.target.style.display = 'none'}
              />
            </div>
            <div className="pastor-info">
              <h3 className="pastor-title">{churchInfo.pastor.title}</h3>
              <h2 className="pastor-name">{churchInfo.pastor.name}</h2>
              <p className="pastor-bio">{churchInfo.pastor.bio}</p>
              <p className="pastor-message">
                <strong>A Word from Our Pastor:</strong><br/>
                "I believe that every person matters to God. Whether you've walked with Jesus for years 
                or you're just beginning to explore faith, you belong here. We're committed to creating 
                a community where people encounter Christ authentically and grow in their faith journey."
              </p>
            </div>
          </div>
        </div>
      </section>

      {/* Ministries Section */}
      <section className="ministries-section">
        <div className="container">
          <div className="section-title">
            <h2>Our Ministries</h2>
            <p>Find your place to serve and grow</p>
          </div>
          <div className="grid grid-4">
            {featuredMinistries.map((ministry) => (
              <MinistryCard key={ministry.id} ministry={ministry} />
            ))}
          </div>
          <div className="text-center mt-4">
            <Link to="/ministries" className="btn btn-primary">
              Explore All Ministries
            </Link>
          </div>
        </div>
      </section>

      {/* Latest Sermons Section */}
      <section className="sermons-section section-light">
        <div className="container">
          <div className="section-title">
            <h2>Latest Sermons</h2>
            <p>Grow in your faith with God's Word</p>
          </div>
          <div className="grid grid-3">
            {latestSermons.map((sermon) => (
              <SermonCard key={sermon.id} sermon={sermon} />
            ))}
          </div>
          <div className="text-center mt-4">
            <Link to="/sermons" className="btn btn-primary">
              Browse All Sermons
            </Link>
          </div>
        </div>
      </section>

      {/* Upcoming Events Section */}
      <section className="events-section">
        <div className="container">
          <div className="section-title">
            <h2>Upcoming Events</h2>
            <p>Never miss what's happening at LFCC Kenya</p>
          </div>
          <div className="grid grid-3">
            {upcomingEvents.map((event) => (
              <EventCard key={event.id} event={event} />
            ))}
          </div>
          <div className="text-center mt-4">
            <Link to="/events" className="btn btn-primary">
              See All Events
            </Link>
          </div>
        </div>
      </section>

      {/* Testimonials Section */}
      <section className="testimonials-section section-light">
        <div className="container">
          <div className="section-title">
            <h2>Member Stories</h2>
            <p>See how God is working in our community</p>
          </div>
          <div className="grid grid-3">
            <div className="testimonial-card">
              <div className="testimonial-rating">★★★★★</div>
              <p className="testimonial-text">
                "LFCC Kenya changed my life. The community, the teaching, and the love I experienced here 
                helped me get closer to God than ever before."
              </p>
              <p className="testimonial-author">— Sarah M.</p>
            </div>
            <div className="testimonial-card">
              <div className="testimonial-rating">★★★★★</div>
              <p className="testimonial-text">
                "I came as a skeptic, but the authentic faith and genuine care from the church family 
                convinced me that Jesus is real and that God loves me unconditionally."
              </p>
              <p className="testimonial-author">— David K.</p>
            </div>
            <div className="testimonial-card">
              <div className="testimonial-rating">★★★★★</div>
              <p className="testimonial-text">
                "The ministries here are incredible. I found my place in the youth group and discovered 
                my purpose in serving others."
              </p>
              <p className="testimonial-author">— Janet N.</p>
            </div>
          </div>
        </div>
      </section>

      {/* Call to Action Section */}
      <section className="cta-section">
        <div className="container">
          <div className="cta-content">
            <h2>Ready to Connect?</h2>
            <p>
              Whether you're looking to worship with us, join a ministry, or just want to learn more about 
              Living Faith Community Church Kenya, we'd love to meet you.
            </p>
            <div className="cta-buttons">
              <Link to="/services" className="btn btn-secondary btn-large">
                Visit Us This Sunday
              </Link>
              <Link to="/contact" className="btn btn-light btn-large">
                Get in Touch
              </Link>
            </div>
          </div>
        </div>
      </section>
    </main>
  );
}
