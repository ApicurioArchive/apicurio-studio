# Migration Guide: Apicurio Studio to Apicurio Registry

This guide provides information for migrating from the standalone Apicurio Studio to Apicurio Registry's integrated Studio functionality.

## Overview

**Apicurio Studio has been deprecated** and its functionality has been fully integrated into [Apicurio Registry](https://github.com/Apicurio/apicurio-registry) starting with **Registry version 3.1**. The Registry now provides all Studio capabilities as part of its web UI, offering a unified platform for API registry and design.

## Key Changes

### What's Different

1. **Unified Platform**: Studio functionality is now part of the Registry UI rather than a standalone application
2. **Integrated Storage**: API designs are stored directly in the Registry alongside other artifacts
3. **Enhanced Integration**: Better integration with Registry features like schema validation, compatibility rules, and governance
4. **Single Deployment**: No need to deploy and maintain separate Studio and Registry instances

### What Remains the Same

- **API Design Experience**: The core API design and editing capabilities remain functionally equivalent
- **OpenAPI & AsyncAPI Support**: Full support for OpenAPI 2.x/3.x and AsyncAPI specifications
- **Visual Editor**: The same intuitive visual editing interface for API specifications
- **Import/Export**: Ability to import existing API designs and export completed specifications

## Migration Paths

### For New Installations

**Recommended**: Deploy Apicurio Registry 3.1 or later instead of Apicurio Studio.

- **Repository**: https://github.com/Apicurio/apicurio-registry
- **Documentation**: https://www.apicur.io/registry/docs/
- **Container Images**: Available on Quay.io and Docker Hub as `apicurio/apicurio-registry:3.1.0` or later
- **Minimum Version**: Apicurio Registry 3.1+ required for integrated Studio functionality

### For Existing Apicurio Studio Users

#### Option 1: Fresh Start (Recommended)
1. Deploy Apicurio Registry
2. Re-import your API designs into Registry
3. Continue development using Registry's integrated Studio UI
4. Decommission standalone Studio instance

#### Option 2: Data Migration
If you have significant API design data in Studio:

1. **Export API Designs**: Export all API designs from your current Studio instance
   - Use Studio's export functionality to download OpenAPI/AsyncAPI files
   - Ensure you have local copies of all important designs

2. **Deploy Apicurio Registry 3.1+**: Set up a new Registry instance
   - Follow Registry installation documentation
   - Ensure you deploy version 3.1 or later for Studio integration
   - Configure according to your requirements (storage, security, etc.)

3. **Import to Registry**: Upload your API designs to Registry
   - Use Registry's UI or REST API to import your exported designs
   - Designs will be automatically available in the integrated Studio interface

4. **Verify Migration**: Test that all designs work correctly in Registry's Studio interface

5. **Update Integrations**: Update any CI/CD pipelines or tooling to point to Registry instead of Studio

## Deployment Information

### System Requirements

Apicurio Registry has similar system requirements to Studio but provides additional capabilities:

- **Memory**: 1GB+ RAM recommended (vs. Studio's requirements)
- **Storage**: Database or persistent storage for artifact persistence
- **Network**: HTTP/HTTPS access for UI and REST API

### Installation Options

1. **Container Deployment** (Recommended)
   ```bash
   docker run -p 8080:8080 apicurio/apicurio-registry:3.1.0
   ```

2. **Kubernetes/OpenShift**
   - Use official Helm charts or operators
   - Production-ready configurations available

3. **Cloud Deployments**
   - Compatible with major cloud platforms
   - Supports various storage backends (PostgreSQL, H2, etc.)

### Configuration

Key configuration differences from standalone Studio:

- **Storage Backend**: Registry requires a storage backend configuration
- **Authentication**: Supports various auth methods (OIDC, basic auth, etc.)
- **Studio UI**: Automatically enabled - no separate Studio deployment needed

## Feature Mapping

| Studio Feature | Registry Equivalent | Notes |
|----------------|---------------------|-------|
| API Design UI | Integrated Studio UI | Same functionality, integrated experience |
| Project Management | Registry Groups/Artifacts | Enhanced organization capabilities |
| Import/Export | Registry Import/Export | Supports additional formats |
| Collaboration | Registry Sharing + Comments | Enhanced collaboration features |
| Version Management | Registry Versions | More robust versioning system |

## Support and Resources

### Documentation
- **Registry Documentation**: https://www.apicur.io/registry/docs/
- **Studio Integration Guide**: Available in Registry documentation
- **API Reference**: Complete REST API documentation for Registry

### Community
- **GitHub Issues**: https://github.com/Apicurio/apicurio-registry/issues
- **Community Chat**: https://apicurio.zulipchat.com/
- **Mailing Lists**: Available through Apicurio community channels

### Getting Help

If you encounter issues during migration:

1. **Check Registry Documentation**: Most common scenarios are documented
2. **Search Existing Issues**: Look for similar migration questions on GitHub
3. **Create New Issue**: Provide details about your specific migration scenario
4. **Community Support**: Reach out via community chat for real-time help

## Timeline

- **Apicurio Studio**: No longer maintained (deprecated)
- **Security Updates**: Critical security issues may receive patches temporarily
- **End of Life**: Plan to complete migration as soon as feasible
- **Apicurio Registry**: Active development and long-term support

## Conclusion

Migrating to Apicurio Registry provides a more robust, feature-rich platform while maintaining the API design capabilities you rely on. The integrated approach simplifies deployment and provides better long-term support.

For questions or migration assistance, please reach out to the Apicurio community or file an issue in the Registry repository.